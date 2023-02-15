pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/tirush1245/Laravel-Demo.git'
                sh 'composer install'
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'         
             }
        }
        stage('Test') {
            steps {
                sh './vendor/bin/phpunit'
            }
        }
        stage('Deploy') {
            steps {
			    sh 'chmod -R 777 /var/jenkins_home/workspace/'							
                sh 'rsync -avz . root@ec2-43-205-144-0.ap-south-1.compute.amazonaws.com:/var/www/websites/laravel-V9/'
			}
		 }
    }        
}
