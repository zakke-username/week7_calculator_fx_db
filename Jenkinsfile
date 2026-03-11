pipeline {
    agent any
    environment {
        IMAGE_NAME = "zakkedocker/sum-product-fx"
        IMAGE_TAG = "latest"
    }
    stages {
        stage('Build jar') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Build docker image') {
            steps {
                script {
                    bat "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                }
            }
        }
        stage('Docker compose') {
            steps {
                script {
                    bat "docker compose down -v"
                    bat "docker compose up --build"
                }
            }
        }
    }
}