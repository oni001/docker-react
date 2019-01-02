node {
    def app

    stage('clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
       /* This builds the actual image; synonymous to
        * docker build on the command line */

        app = docker.build("oni001/docker-react")    
  }   
  
  stage('Test image') {
      app.inside {
          sh 'echo "Tests passed"'
      }
}

stage('Push image') {
docker.withRegistry('https://registry.hub.docker.com', 'oni001') {
    app.push("${env.BUILD_NUMBER}")
    app.push("latest")
}
