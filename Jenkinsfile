pipeline {
    agent {
        label  ' agent'
    }
    tools{
        maven 'maven362'
    }
   stages{
        stage('git checkout'){
            steps{
               git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
        stage('build'){
            steps{
                sh "mvn clean install"
            }
        }
       stage('deploy'){
            steps{
                ansiblePlaybook credentialsId: 'docker-ssh-key', disableHostKeyChecking: true, inventory: '/etc/ansible/hosts', playbook: 'Deploying.yml'
            }
        }
        
    }
}
