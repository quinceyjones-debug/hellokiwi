pipeline {
  agent any
  tools { jdk 'JDK17' }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
        bat 'dir /b'
      }
    }
    stage('Build') {
      steps {
        bat '.\\mvnw.cmd -B -v'
        bat '.\\mvnw.cmd -B clean package -DskipTests'
      }
    }
  }
  post {
    success { archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true }
  }
}
