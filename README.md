rpi-jupyter
===

Docker container with python Environment for raspberry-pi3

Install Stable Docker Community Edition
--------------------------------------------------------------

For RaspberryPi3: https://www.raspberrypi.org/blog/docker-comes-to-raspberry-pi/

Running container for the first time
--------------------------------------------------------------

First run `docker pull rh02/rpi-jupyter` to pull the latest version of image. Run using `docker run -it -p 8080:8080 --name notebook rh02/rpi-jupyter`. This command downloads the prepared image from a public hub, and starts a bash for you.

## Stopping and starting the container

This "stop and start" scenario is useful when you want to take a break and turn off your host machine.

### Stopping the container

Save your work inside the container, then run `docker stop notebook` in different terminal window to stop a running container. You will be able to start it later.

### Starting container after stopping

Run `docker start -a notebook` to run previously stopped container and attach to its stdout. You can continue to work where you left off.

## Container checkpoints

You might want to make a checkpoint of your work so that you can return to it later. Think of it as a backup or commit in version control system.

### Saving container state

You will first have to stop the container following instructions above. Now you need to save the container state so that you can return to it later: `docker commit notebook notebook-snap`. You can make sure that it's saved by running `docker images`.

### Creating new container from previous checkpoint

If you want to continue working from a particular checkpoint, you should run a new container from your saved image by executing `docker run -it --name notebook2 notebook-snap`. Notice that we incremented index in the container name, because we created a new container.



