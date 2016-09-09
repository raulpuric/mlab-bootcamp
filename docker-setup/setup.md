# Docker and IPython Setup

## Docker Setup
Download Docker Toolbox at https://www.docker.com/products/docker-toolbox.

Follow instructions at: <br />
Mac OSX - https://docs.docker.com/toolbox/toolbox_install_mac/ <br />
Windows - https://docs.docker.com/toolbox/toolbox_install_windows/

## IPython Setup
1. Run Docker Quick Start Terminal to start your Docker terminal
2. Make sure your VM is running: <br />
  ```
    docker version
  ```
3. If it says "Cannot connect to the Docker daemon. Is 'docker -d' running on this host?", run: <br />
  ```
    docker-machine rm default
    docker-machine create default --driver virtualbox
  ```
4. Set up Docker container with needed resources (NumPy, SciPy, Pandas): <br />
  ```
    docker run -d -p 8888:8888 jupyter/datascience-notebook start-notebook.sh
  ```
5. Check your "DOCKER_HOST"  with "docker-machine env default"
6. Set your environment variables <br />
  ```
    eval $(docker-machine env default)
  ```
7. Go to your default browser and type "https://{VM_host_id}:8888"
8. Enjoy Jupyter Notebook!

## Get Assignments 
1. Open "New > Terminal" within your IPython browser
2. Clone the ml-b-bootcamp repository for assignments <br />
  ```
    git clone https://github.com/jpark96/ml-b-bootcamp.git
  ```
3. Download mlxtend <br />
  ```
    pip install mlxtend
  ```
3. Change directories to "ml-b-bootcamp/assignments"
4. Open the assignment!

## Saving docker image
You will lose all changes within your Docker container/VM if you do not commit your code to the Docker Engine. In order to prevent this, do: <br />
1. Find name of your running container: <br />
  ```
    docker ps
  ```
2. Save this container as an image: <br />
  ```
    docker commit <container_name> <desired_image_name>
  ```

Later, when you want to load the image, run: <br />
```
  docker run -d -p 8888:8888 <image_name> start-notebook.sh
```

Additional Resources: <br />
1. Docker Containers: https://docs.docker.com/v1.10/engine/userguide/containers/dockerrepos/
