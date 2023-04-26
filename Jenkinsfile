try {
  stage("Building SONAR …") {
    sh ‘./gradlew clean sonarqube’
  }
} catch (e) {
  emailext attachLog: true, body: ‘See attached log’, subject: ‘BUSINESS Build Failure’, to: ‘abc@gmail.com’
  step([$class: ‘WsCleanup’])
   return
}

Add the following plugin details in the build.gradle/pom.xml file (if it is maven):
a) Sonar Plugin
dependencies {
  classpath "org.sonarsource.scanner.gradle: sonarqube-gradle-plugin:2.5"
}

b) Apply plugin: ‘org.sonarqube’
c) Add SonarQube Server Details:
sonarqube {
properties {
  property "sonar.host.url", http://sonar.xxxxx.com // url is your sonar server
    property "sonar.projectName", "project display name" // this name will appear in dashboard
  property "sonar.projectKey", "projectKey" // It sould be a keybased on this report is created
  property "sonar.groovy.jacoco.reportPath", "${project.buildDir}/jacoco/test.exec" }
}
