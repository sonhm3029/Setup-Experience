# CUDA INSTALLATION GUIDE

## INSTALLATION STEP

**Note:** Check version compatible for nvidia-driver, gcc, cuda toolkit, nccl on Nvidia official webpage

Date: 09/07/2024:

- [Link 1](https://docs.nvidia.com/deploy/cuda-compatibility/)
- [Link 2](https://docs.nvidia.com/deploy/cuda-compatibility/)

1. Install nvidia driver
2. Install gcc
3. Install cudatoolkit
4. Install cudnn
5. Install nccl (for multiple gpus)

## INSTALL CUDA 12.2 ON ROCKY LINUX 9

### Download the CUDA repository package

```sh
wget https://developer.download.nvidia.com/compute/cuda/12.2.2/local_installers/cuda-repo-rhel9-12-2-local-12.2.2_535.104.05-1.x86_64.rpm
```

### Install the repository package

```sh
sudo rpm -i cuda-repo-rhel9-12-2-local-12.2.2_535.104.05-1.x86_64.rpm
sudo cp /etc/yum.repos.d/cuda-rhel9-12-2-local.repo /etc/yum.repos.d/cuda.repo
```

### Clean dnf cache

```sh
sudo dnf clean all
```

### Reset the NVIDIA driver module

```sh
sudo dnf module reset nvidia-driver
```

### Enable the specific stream for the NVIDIA driver

```sh
sudo dnf module enable nvidia-driver:535-dkms
```

### Install the NVIDIA driver

```sh
sudo dnf install nvidia-driver
```

### Install CUDA 12.2

```sh
sudo dnf install cuda-12-2
```

### Verify CUDA installation

```sh
nvcc --version
```

### Install cudnn

- Page reference: https://developer.nvidia.com/cudnn-downloads?target_os=Linux&target_arch=x86_64&Distribution=Rocky&target_version=9&target_type=rpm_network

```sh
sudo dnf config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel9/x86_64/cuda-rhel9.repo
sudo dnf clean all
sudo dnf -y install cudnn
```

```sh
sudo dnf -y install cudnn-cuda-12
```
