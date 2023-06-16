pipeline {
    agent any
    tools {nodejs 'node20'}
    environment {
        NODE_ENV='production'
    }
    
    
    
    stages {
            stage('source') {
            steps {
                git 'https://github.com/sandeepkumar1701/aws_codebuild_codedeploy_nodeJs_demo.git'
                sh 'cat index.js'
            }
        }
        
                 stage('build') {
                     environment {
                         NODE_ENV='staging'
                     }
            steps {
                echo NODE_ENV
                withCredentials([string(credentialsId: '9b7eb131-48ea-445a-9693-cdc329eec6d4', variable: 'secver')]) {
                  // some block
                  echo secver
                } 
                sh 'npm install'
            }
        }
              stage('saveArtifact') {
            steps {
                archiveArtifacts artifacts: '**', followSymlinks: false
            }
        }
     
}
}
