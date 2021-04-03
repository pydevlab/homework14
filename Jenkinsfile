pipeline {
  environment {
      registry = “pydevlab/testbuild”
      registryCredential = ‘dockerhub-cred’
      dockerImage = ‘’
  }
  agent any
  stages {
      stage(‘Cloning git repository’) {
          steps {
              git ‘https://github.com/pydevlab/homework14.git’
          }
      }
      stage(‘Building image’) {
          steps{
              script {
                  dockerImage = docker.build registry + “:$BUILD_NUMBER”
              }
         }
      }
      stage(‘Deploy image ‘) {
          steps{
              script {
                  docker.withRegistry( ‘’, registryCredential ) {
                      dockerImage.push()
 
                  }
              }
          }
      }
  }
}
