<h3>Simple Maven template</h3>

mvn test

mvn compile

mvn package

java -jar target/projectname-1.0-SNAPSHOT.jar

or

mvn exec:java

In case you want to create a maven from scratch:
mvn archetype:generate -DgroupId=fi.vamk.studentid -DartifactId=projectname -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false -DarchetypeGroupId=org.apache.maven.archetypes

To be able to run java -jar add a plug-in:

<build>
    <plugins>
      <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.1</version>
          <configuration>
              <source>1.8</source>
              <target>1.8</target>
          </configuration>
      </plugin>
      <!-- enabling java -jar target\javaproject.jar -command -->
      <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-jar-plugin</artifactId>
          <version>3.1.1</version>
          <configuration>
              <archive>
                  <manifest>
                      <mainClass>fi.vamk.studentid.App</mainClass>
                  </manifest>
              </archive>
              <descriptorRefs>
                  <descriptorRef>jar-with-dependencies</descriptorRef>
              </descriptorRefs>
          </configuration>
      </plugin>
      <!-- enabling mvn exec:java -command -->
      <plugin>
          <groupId>org.codehaus.mojo</groupId>
          <artifactId>exec-maven-plugin</artifactId>
          <version>1.5.0</version>
          <configuration>
              <mainClass>fi.vamk.studentid.App</mainClass>
          </configuration>
      </plugin>
    </plugins>  
  </build>
# UNIT_TEST
