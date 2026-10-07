pipeline {
    agent any

    stages {

        stage('Check Docker') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-devops-app:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker rm -f jenkins-devops-app 2>NUL || exit /b 0'
            }
        }

        stage('Run New Container') {
            steps {
                bat 'docker run -d --name jenkins-devops-app -p 5000:5000 jenkins-devops-app:latest'
            }
        }
    }
}