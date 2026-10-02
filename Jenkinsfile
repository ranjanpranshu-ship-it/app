pipeline {
    agent any
    environment {
        NODE_ENV = 'production'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ranjanpranshu-ship-it/app.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Docker Build & Push') {
            steps {
                sh 'docker build -t my-registry/my-nestjs:latest .'
                sh 'docker push my-registry/my-nestjs:latest'
            }
        }
    }
    post {
        success { echo '✅ Build succeeded!' }
        failure { echo '❌ Build failed!' }
    }
}   