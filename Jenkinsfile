pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting project files from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker Application'
                bat 'docker compose build'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application'
                bat 'docker compose up -d'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'docker compose ps'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }

        failure {
            echo 'Application deployment failed!'
        }
    }
}