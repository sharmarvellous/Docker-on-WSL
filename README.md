# Docker on WSL (Windows Subsystem for Linux)

This guide covers the steps to set up Docker on Windows Subsystem for Linux (WSL) in a Windows 11 environment.

## Prerequisites

1. **Windows 11**: Ensure you are running Windows 11, as WSL is a feature introduced in Windows 10 and further improved in Windows 11.
2. **WSL Installation**: Install the Windows Subsystem for Linux (WSL) by running the following command in PowerShell or Command Prompt:
   wsl --install
This command will enable the necessary features and install the default Ubuntu distribution of Linux.

## Setting up Docker on WSL

1. **Start the Ubuntu WSL instance**: You should be able to see the "Ubuntu" (or the Linux distribution you selected) app in your Windows Start menu. Click on it to launch the WSL environment.

2. **Install Docker in Ubuntu WSL**:

  a. Update the package lists:
     sudo apt-get update
  b. Install the necessary dependencies:
     sudo apt-get install ca-certificates curl
  c. Add Docker's official GPG key:
     sudo install -m 0755 -d /etc/apt/keyrings
     sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
     sudo chmod a+r /etc/apt/keyrings/docker.asc
  d. Add the Docker repository to Apt sources:
     echo
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu 
     $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | 
     sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  e. Install Docker packages:
     sudo apt-get update
     sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

3. **Verify Docker installation**:
   sudo docker run hello-world
This command should pull and run the "hello-world" Docker image, verifying that Docker is installed and functioning correctly.

## Understanding the WSL, Sandbox, and Docker Relationship

1. **WSL (Windows Subsystem for Linux)**: This is a feature in Windows 10 and later that allows you to run Linux command-line tools and utilities directly on your Windows machine. It creates a Linux environment within Windows, providing a seamless integration between the two operating systems.

2. **Sandbox**: The Ubuntu VM (or any other Linux distribution) running within WSL can be considered a sandbox, providing a separate, isolated environment for running Linux applications.

3. **Docker**: If you install Docker within the Ubuntu WSL, you can use it to create and manage containers within that sandboxed environment.

In summary, WSL provides a way to create a sandboxed Linux environment within Windows, and you can use tools like Docker within that sandbox to create and manage containers.

## Additional Resources

- [Microsoft Learn: Getting Started with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
- [Docker Documentation: Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
