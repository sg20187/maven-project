pipeline {
    agent any

//    triggers {
//         pollSCM('* * * * *')
//    } 

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging'){
            steps {
                build job: 'deploy-app-pipeline'
            }
	}
    }
}
