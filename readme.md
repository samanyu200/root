Ubuntu 22.04 QEMU Virtual Machine in Docker Container
Docker Ubuntu QEMU

A lightweight Ubuntu 20.04 virtual machine running in a Docker container using QEMU/KVM for optimal performance.

Features
🐳 Containerized Ubuntu 22.04 VM
⚡ KVM-accelerated for near-native performance
🌐 Web-based VNC access (port 6080)
🔑 SSH access (port 2221)
💾 Persistent storage volume
Prerequisites
Docker installed
KVM support on host machine
sudo privileges (for KVM device access)
VM user and pass
username:- root
password:- root
Installation
# Clone the repository
git clone https://github.com/samanyu200/root/
cd root

# Build the Docker image
docker build -t ubuntu-vm .

# Run the container

docker run --privileged -p 6080:6080 -p 2221:2222 -v $PWD/vmdata:/data ubuntu-vm

🐳 To Run in NAT Mode (default):
bash


docker run --privileged -p 6080:6080 -p 2222:2222 -v $PWD/vmdata:/data ubuntu-vm


🔁 To Run in Bridge Mode:
bash


docker run --privileged -e NETWORK_MODE=bridge -e BRIDGE_IF=br0 -p 6080:6080 -v $PWD/vmdata:/data ubu


# or

docker build -t ubuntu-vm .

docker run --rm --privileged --net=host -v $PWD/vmdata:/data ubuntu-vm
