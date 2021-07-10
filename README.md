# Nvidia-TLT-Installation



## Docker Installation
```
sudo apt-get remove docker docker-engine docker.io containerd runc 
```
**If *docker-engine* cause error you can delete it**
```
sudo apt-get update
```
```
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```
sudo apt-get update
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
```
sudo docker run hello-world 
```


### Docker Post Installation Steps
```
sudo groupadd docker
```
```
sudo usermod -aG docker $USER  
```
**Logout and login**
```
newgrp docker
```
**Verify worked without sudo**
```
docker run hello-world 
```


## Container Toolkit Installation
```
curl https://get.docker.com | sh && sudo systemctl --now enable docker
```
```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo  apt-key add - && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```
**Below line is for experimental features**
```
curl -s -L https://nvidia.github.io/nvidia-container-runtime/experimental/$distribution/nvidia-container-runtime.list | sudo tee /etc/apt/sources.list.d/nvidia-container-runtime.list 
```
```
sudo apt-get update
```
```
sudo apt-get install -y nvidia-docker2
```
```
sudo systemctl restart docker
```
```
sudo docker run --rm --gpus all nvidia/cuda:11.0-base nvidia-smi
```
**Excepted output:**
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.42.01    Driver Version: 470.42.01    CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  On   | 00000000:01:00.0 Off |                  N/A |
| N/A   62C    P0    16W /  N/A |    401MiB /  3911MiB |      4%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
+-----------------------------------------------------------------------------+
```
**Go to [NGC](https://ngc.nvidia.com/) website and click on your username in the upper right corner -> click setup -> click generate api key and copy the API key**
```
docker login nvcr.io
```
**Username: $oauthtoken**

**Password: API KEY**



## TLT Installation
```
sudo apt install python3-venv -y
```
```
python3 -m venv launcher
```
```
source launcher/bin/activate
```
```
pip3 install nvidia-pyindex
```
```
pip3 install nvidia-tlt
```
**Use *source launcher/bin/activate* when you want to use TLT**









