---
title: "No Device Supporting CUDA on Ubuntu 10.04 x86_64"
date: 2010-07-18
forum: Multimedia Software
---

### Post by mohammadsamani on 2010-07-18
I have the 64-bit Ubuntu 10.04, installed on a Desktop computer (version 2.6.32-23-generic)
I also have an NVIDIA card that supports CUDA. These two lines are from lspci:

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

Here is what I have tried:

Removed NVIDIA drivers from my system.  (sudo apt-get --purge remove nvidia-*, devdriver* --uninstall)
Rebooted,
GRUB -> Recovery mode,
telinit 3
Installed the CUDA Dev Driver there
Rebooted.
Then I installed CUDA toolkit, and SDK
Ran Make command in SDK/C folder
Executed deviceQuery and got the following message:

There is no device supporting CUDA

I tried the above procedure with the following combinations:

gcc 4.4, CUDA Driver 3.1, CUDA Toolkit, 3.1, SDK 3.1
gcc 4.3, CUDA Driver 3.1, CUDA Toolkit, 3.1, SDK 3.1
gcc 4.3, CUDA Driver 3.0, CUDA Toolkit, 3.0, SDK 3.0
gcc 4.4, CUDA Driver 3.0, CUDA Toolkit, 3.0, SDK 3.0

If I try to run make command in SDK using gcc 4.4, it won't compile, since NVIDIA does not support gcc 4.4 yet. I can, however, install the driver with gcc 4.4 successfully.

Other observations:

System -> Administration -> Hardware Driver does not show any proprietary hardware drivers.

All fancy graphic features of Ubuntu works, so I have a working graphics driver.

CUDA was working on the same installation of Ubuntu until a while ago. I am not sure what exactly caused it to not work, but my guess is, after I attempted a "Partial Upgrade" it stopped working.

echo $LD_LIBRARY_PATH
:/usr/local/cuda/lib64:/usr/local/cuda/lib

echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/cuda/bin

I would appreciate any suggestions, guesses, or previous similar experience that might lead to a solution.

---

### Post by mohammadsamani on 2010-07-19
I just tried the whole process with gcc 4.4 and CUDA 3.1 package (Driver, toolkit, SDK)
I was able to compile all sample codes in the SDK, but when I execute the deviceQuery file, I get the following error:

 CUDA Device Query (Runtime API) version (CUDART static linking)

cudaGetDeviceCount FAILED CUDA Driver and Runtime version may be mismatched.

FAILED

NVIDIA suggested that $LD_LIBRARY_PATH is not set properly but it is for me:

$ echo $LD_LIBRARY_PATH
:/usr/local/cuda/lib64:/usr/local/cuda/lib

---

### Post by gabe_rosser on 2010-07-24
Same problem here.  I'm running Ubuntu 10.04 x86_64.

I'm quite new to this so I wasn't totally sure how to install it.  Here's what I did (and didn't do):

- Install toolkit using sudo (Ubuntu 9.10 version - is that correct?).
- Add nvcc directory to PATH and export LD_LIBRARY_PATH.
- Compile SDK.  A few problems here: had to manually create a symbolic link to /usr/lib/nvidia-current/libcuda.so in /usr/local/cuda/lib64.  No idea why - is this because I'm using an old graphics driver?  All compiled successfully after this.
- Haven't installed any new graphics driver, I'm using 195.36.24 according to nvidia-settings


> **mohammadsamani said:**
> I just tried the whole process with gcc 4.4 and CUDA 3.1 package (Driver, toolkit, SDK)
I was able to compile all sample codes in the SDK, but when I execute the deviceQuery file, I get the following error:

 CUDA Device Query (Runtime API) version (CUDART static linking)

cudaGetDeviceCount FAILED CUDA Driver and Runtime version may be mismatched.

FAILED


---

### Post by mohammadsamani on 2010-07-24
I think you will need the Development drivers and not the normal NVIDIA drivers.

Did you have problem compiling the SDK sample codes? That doesn't have anything to do with your graphic card. You can compile the SDK without having an NVIDIA graphic card.

Does your card has CUDA capabilities? Is it listed in CUDA enabled cards on NVIDIA sites?

[http://www.nvidia.com/object/cuda_gpus.html](http://www.nvidia.com/object/cuda_gpus.html)

---

### Post by gabe_rosser on 2010-07-25
I have a GTX275, it is CUDA-enabled.

The SDK sample codes all compiled fine.  I originally had an error linking libcuda.so when compiling matrixMulDrv (this would probably have been an issue downstream with further code too).  I found the library in /usr/lib/nvidia-current/libcuda.so so I just made a symlink in the cuda lib64 folder, which fixed it.

So you think I must have the development drivers installed?  I just have the 'normal' ones installed at the moment.

Is there a guide to installing these drivers?  I *hate* messing with graphics drivers - have had so much trouble with it in the past :(

---

### Post by gabe_rosser on 2010-07-25
OK, I have checked again.

deviceQuery still returns an error: 

```
gabs@fred:~/NVIDIA_GPU_Computing_SDK/C/bin/linux/release$ ./deviceQuery
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

cudaGetDeviceCount FAILED CUDA Driver and Runtime version may be mismatched.

FAILED

Press <Enter> to Quit...
```

devQueryDrv works:

```
gabs@fred:~/NVIDIA_GPU_Computing_SDK/C/bin/linux/release$ ./deviceQueryDrv 
CUDA Device Query (Driver API) statically linked version 
There is 1 device supporting CUDA

Device 0: "GeForce GTX 275"
  CUDA Driver Version:                           3.0
  CUDA Capability Major revision number:         1
  CUDA Capability Minor revision number:         3
  Total amount of global memory:                 938803200 bytes
  Number of multiprocessors:                     30
  Number of cores:                               240
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       16384 bytes
  Total number of registers available per block: 16384
  Warp size:                                     32
  Maximum number of threads per block:           512
  Maximum sizes of each dimension of a block:    512 x 512 x 64
  Maximum sizes of each dimension of a grid:     65535 x 65535 x 1
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             256 bytes
  Clock rate:                                    1.49 GHz
  Concurrent copy and execution:                 Yes
  Run time limit on kernels:                     Yes
  Integrated:                                    No
  Support host page-locked memory mapping:       Yes
  Concurrent kernel execution:                   No
  Device has ECC support enabled:                No

PASSED

Press ENTER to exit...
```

Every other binary I try to run returns a different error:

```
gabs@fred:~/NVIDIA_GPU_Computing_SDK/C/bin/linux/release$ ./particles 
./particles Starting...

grid: 64 x 64 x 64 = 262144 cells
particles: 16384
particleSystem.cu(80) : cudaSafeCall() Runtime API error : CUDA driver version is insufficient for CUDA runtime version.
```

...Not too hard to guess that my driver is the wrong one?

Interestingly, matrixMulDrv also works, presumably because it's a statically-linked binary?  The rest have shared libraries.

---

### Post by mohammadsamani on 2010-07-25
I eventually got it to work by install cuda toolkit, and sdk version 2.3, instead of 3.0 or 3.1.
When compiling the sdk, make sure your gcc version is 4.3 and not 4.4.

> update-alternatives --config gcc

---

### Post by gabe_rosser on 2010-07-25
Got mine working as well now - as suspected I needed to install a newer nVidia driver.  Now using the development drivers 256.40.  I followed the instructions [here]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html").

I have to admit I don't really know what the modprobe blacklist part does.

CUDA Toolkit 3.1, compiled with gcc version 4.4.3.  I thought that isn't supposed to work??

Anyway, thanks very much for your help here.

---

