pipeline{
    agent any
	parameters {
         string(name: 'staging_server', defaultValue: '10.0.4.115', description: 'Remote Staging Server')
    }
	tools{
        maven 'maven'
    }
    stages{
        stage ('Build'){
            steps{
                bat 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{

                echo "Deployment"
            }
		stage{
			bat 'copy StrictHostKeyChecking=no **/*.war root@${params.staging_server}:D:\\Gen\\Tom\\tom_test\\webapps\\'
		}
        }
    }
}
    

