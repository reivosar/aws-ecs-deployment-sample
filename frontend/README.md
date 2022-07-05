## Getting Started

Requirement:
- AWS Account
- IAM user with AdministratorAccess privileges
- AWS CLI version 2 (click here for local installation instructions)

<hr>

1. Obtain an authentication token and authenticate the Docker client against the registry.

```
aws ecr get-login-password --region ap-northeast-1 | docker login --username AWS --password-stdin XXXXXXXX.dkr.ecr.ap-northeast-1.amazonaws.com
```

2. Create a private repository with the aws ecr create-repository command.

```
aws ecr create-repository \
    --repository-name hello-node-app \
    --region ap-northeast-1
```

3. Build a Docker image.

```
docker build -t XXXXXXXX/aws-ecs-deployment-sample-frontend .
```

4. Tag the built Docker image.

```
docker tag aws-ecs-deployment-sample-frontend:latest XXXXXXXX.dkr.ecr.ap-northeast-1.amazonaws.com/aws-ecs-deployment-sample-frontend:latest
```

5. Push Docker image to ECR.

```
docker push XXXXXXXX.dkr.ecr.ap-northeast-1.amazonaws.com/XXXXXXXX/aws-ecs-deployment-sample-frontend:latest
```