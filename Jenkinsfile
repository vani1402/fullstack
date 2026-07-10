pipeline {

    agent any

    stages {

        stage('Checkout') {

            steps {

                checkout scm

            }

        }

        stage('Build Backend') {

            steps {

                sh 'docker build -t backend-image ./backend'

            }

        }

        stage('Build Frontend') {

            steps {

                sh 'docker build -t frontend-image ./frontend'

            }

        }

        stage('Deploy') {

            steps {

                sh 'docker compose down || true'

                sh 'docker compose up -d --build'

            }

        }

    }

    post {

        success {

            echo 'Deployment Successful'

        }

        failure {

            echo 'Deployment Failed'

        }

    }

}