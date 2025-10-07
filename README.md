# Hello Docker (Spring Boot)

Minimal Spring Boot project to learn Docker image build and run.

## Option A: Local build + simple Dockerfile
1) Build the jar locally:
```bash
mvn clean package -DskipTests
```
2) Build the image:
```bash
docker build -t hello-docker:1.0 .
```
3) Run the container:
```bash
docker run -d -p 8080:8080 --name hello hello-docker:1.0
```
4) Test:
Open http://localhost:8080 or
```bash
curl http://localhost:8080/
```
5) Logs / stop:
```bash
docker logs -f hello
docker stop hello && docker rm hello
```

## Option B: Multi-stage build (build inside Docker)
1) Build the image (no Maven installed on host required):
```bash
docker build -f Dockerfile.multi -t hello-docker:1.0 .
```
2) Run:
```bash
docker run -d -p 8080:8080 --name hello hello-docker:1.0
```

## Useful Docker commands
```bash
docker images
docker ps
docker exec -it hello sh
docker rm -f hello
docker rmi hello-docker:1.0
```

## Notes
- Uses Java 17 and Spring Boot 3.x
- If port 8080 is already used on your machine, map a different host port like: `-p 9090:8080`
