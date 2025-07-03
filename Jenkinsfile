@Library('Shared')_
pipeline {
    agent {
        label "agent-1"
    }
   stages {
       stage("Code") {
        steps {
            git_clone("https://github.com/prototype-raj/django-notes-app.git", "dev")
        }
    }
    stage("Build") {
        steps {
            docker_build("notes-app", "latest")
        }
    }   
    stage("Push to artifact registry") {
        steps {
            docker_push("notes-app", "latest")
        }
    }
    stage("Deploy") {
        steps {
            docker_compose_build()
        }
    }
   }
}
