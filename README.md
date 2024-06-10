---
runme:
  id: 01J00RCN7NFSHSJP9RT541ASX2
  version: v3
---

## Basic Bash Script

```sh {"id":"01J00RD7ZC7KPH8SGNAEH4JN51"}
echo "Hello! Please enter your name"
read name

#Greet the user
echo "Hello, $name! Welcome to the Bash Scripting World"
```

## Variable Manipulation

```sh {"id":"01J00RCPR8T9KTQM0JQ1EZVZ6G"}
sentence="The quick brown fox jumps over the lazy dog"
echo ${sentence:4:5}

first_name="John"
last_name="Doe"
full_name="$first_name $last_name"
echo $full_name

sentence="The quick brown fox jumps over the lazy dog"
echo ${sentence/brown/yellow}

name="Alice"
echo $name | tr '[:lower:]' '[:upper:]'
echo $name | tr '[:upper:]' '[:lower:]'
echo ${#name}
```

## Conditional Statment

```sh {"id":"01J00REDPY3ZEFYZXY71WZ0TRH"}
echo -n "Enter your score: "
read score

# Perform grade determination based on the score
if (( score >= 90 )); then
  echo "Your grade is A."
elif (( score >= 80 )); then
  echo "Your grade is B."
elif (( score >= 70 )); then
  echo "Your grade is C."
elif (( score >= 60 )); then
  echo "Your grade is D."
else
  echo "Your grade is F."
fi
```

## Bash Script and Docker

```sh {"id":"01J00RFDHC8WMRH2YTGC3XT6QH"}
CONTAINER_NAME="my-nginx-container"
IMAGE_NAME="nginx:latest"


if [ "$(docker ps -a -q -f name=$CONTAINER_NAME)" ]; then
    echo "Removing existing container: $CONTAINER_NAME"
    docker rm -f $CONTAINER_NAME
fi

echo "Running Docker container: $CONTAINER_NAME"
docker run --name $CONTAINER_NAME -d -p 8080:80 $IMAGE_NAME

docker cp local_file.txt $CONTAINER_NAME:/usr/share/nginx/html/file.txt

docker exec $CONTAINER_NAME ls -l /usr/share/nginx/html

docker stop $CONTAINER_NAME

docker rm $CONTAINER_NAME

echo "Script Completed"
```