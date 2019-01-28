```
curl -v -X POST "http://localhost:8282/actuator/bus-refresh"
```


```
curl -v -X POST "http://localhost:8282/actuator/refresh"
```

Client dependency

```
<dependencies>
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-config</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-bus-amqp</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>
```

bootstrap.properties

```
spring.application.name=configclient2
spring.cloud.config.uri=http://localhost:8888
spring.cloud.config.fail-fast=true
spring.profiles.active=prod
```


Don't forget @RefreshScope


Server

```
server.port=8888
spring.cloud.config.server.git.uri=file://${user.home}/cloud-workspace/spring-cloud-config-repo
spring.profiles.active=dev,prod
```
