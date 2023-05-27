pipeline {
    agent any
    
    tools {
     maven "Maven"
     jdk "Java11"
}

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }
    
    stages {
        stage('Hello') {
            steps {
                echo "database engine is ${DB_ENGINE}"
                echo "disable:auth is ${DISABLE_AUTH}"
                echo 'Hello World'
            }
        }
        stage('git Polling') {
            steps {
                git branch: 'master', url: 'https://github.com/sco-github/time-tracker'
            }    
        }
        stage('build con Maven') {
            steps {
                bat "mvn clean package"
            } 
            post {
                success {
                    echo 'Archivar Artefactos'
                    archiveArtifacts "core/target/*.jar"
                    archiveArtifacts "web/target/*.war"
                }
            }
            
        }
        
    }
}
