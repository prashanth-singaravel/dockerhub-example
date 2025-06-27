pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('prashanthsingaravel-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh '/usr/local/bin/docker build -t prashanthsingaravel-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | usr/local/bin/docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh '/usr/local/bin/docker push prashanthsingaravel-alpine:latest'
      }
    }
  }
  post {
    always {
      sh '/usr/local/bin/docker logout'
    }
  }
}
