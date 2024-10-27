pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rohankaranje/intern-ass-2.git'
            }
        }

        stage('Build & Test') {
            parallel {
                stage('Build') {
                    steps {
                        bat 'mvn clean install'
                    }
                }
                stage('Unit Tests') {
                    steps {
                        bat 'mvn test'
                    }
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying the application...'
                // Add your deployment script here
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Build and tests passed!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
