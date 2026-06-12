---
title: "Howto install CUDA 2.3 on Ubuntu 9.04"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Aiyen on 2009-09-15
Okay after spending a few days on doing this myself I figured I would share my findings with other people who might be getting a few grey hairs themselves over this process. 

Another reason why is that while searching while there are a few guides around the web, they are for older versions of CUDA and/or Ubuntu, and all lacked some package etc. So this is mainly suming up a lot of that work into one place. 

I run on a 64bit Ubuntu 9.04, so if someone finds out that something else is needed to make it work on 32bit please feel free to correct me.

Furthermore my machine runs with a single GTX 260 card there may be some complications if you are running a SLI setup.   

I did this on a freshly installed Ubuntu 9.04 only thing I did prior was running update manager to get up to speed and the following first reboot. 

Computer is rebooted, so let us begin. 
First we need to get the CUDA 2.3 files from Nvidia. 
 [http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html)
Fill in the correct OS and get the 190 driver, toolkit and SDK
 
(All the stuff that I do here is for getting all three to work, some steps may not be needed if you are not interested in the SDK.)

Putting the Nvidia files in your home dir for the time being. First we need a bunch of packages in order to make the SDK compile properly. 

open a terminal and put in 

```
sudo apt-get install build-essential libglut3-dev
```

Furthermore we also need to get 3 more packages namely 

libxmu-dev
libxmu-headers 
libxi-dev

These can be installed with sudo apt-get in a terminal or by finding them in synaptic. 

With these downloaded and installed we can continue and install the Nvidia driver. Note that this is on a fresh install and there are more steps to be taken if you are doing it with an older Nvidia driver already installed. There are already posts on the forum about that so I wont go into that here. 

To install the 190 driver on a freshly installed box first open a terminal and put in 

```
chmod +x ./cudadriver_2.3_linux_64_190.18.run
```

Press Ctrl + Alt +  F1 and log in. 

shut down gdm. 

```
sudo /etc/init.d/gdm stop

sudo ./cudadriver_2.3_linux_64_190.18.run
```
Run the installer by and accepting the OpenGL Compatibility, and xconf file question when prompted. 
(You may get a warning when it is searching for conflicting X and OpenGL files, you can only continue and I have not yet had any issues because of it.) 
Once it is done start gdm again by typing in 

```
sudo /etc/init.d/gdm start
```

That should be it for installing the driver. 
Next we need to install the toolkit. To do this we open a terminal and type in 

```
chmod +x ./cudatoolkit_2.3_linux_64_ubuntu9.04.run

sudo ./cudatoolkit_2.3_linux_64_ubuntu9.04.run
```

You get to pick your install directory, here I will assume its in the default. 

The next step is to add the necessary environment variables. In a terminal type in this. (Just type or copy it in one line at a time!)

```
echo "# CUDA stuff 
PATH=\$PATH:/usr/local/cuda/bin
LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:/usr/local/cuda/lib64
export PATH
export LD_LIBRARY_PATH" >> ~/.bashrc

```
Like the toolkit installer says, if you run a 32 bit version you must leave out the 64 part. 

Next we install the SDK. In a terminal type in the following. 

```
chmod +x ./cudasdk_2.3_linux.run
./cudasdk_2.3_linux.run
```

You dont need to be a superuser to install this. 
First you get asked where you want to put the files, and where the CUDA toolkit was installed. (Check that this dir is the same as the one you installed it in, even if it says it located it. The dir need to be the same and not have additions of nvcc or the like!) 

Last we need to compile the SDK files. In a terminal type (I assume default install dir) 

```
cd NVIDIA_GPU_Computing_SDK/C
make 
```

Now it should unpack everything succesfully. You may get a lot of warnings during the process, but these can safely be ignored. 
Once it is done you can test that everything does in fact work by going into
 
```
cd NVIDIA_GPU_Computing_SDK/C/bin/linux/release/
```

and try to run some of the examples in here. Like mentioned in the Nvidia documentation it is a good idead to at least run deviceQuery to verify your CUDA compatible GPU. 

I hope that this may help some aspiring CUDA coders out there, and that I have not typed in a whole lot of nonsense since most of Ubuntu is still new to me. If anyone spots some obvious errors please do correct them.

---

### Post by hoverblade on 2009-09-22
Hello, first I'd like to thank you for this guide, very good job, helped me a lot.

And know, for the my reason of my post, I've followed this guide for a 32 bit Ubuntu and i can confirm it works very well, although, i must point that in my case, as my install was not fresh and i had a previously installed driver, the 180, X failed to start after driver installation, the solution i used was to reboot and remove the old driver, reboot again and then reinstall the 190 and from that on, all went well.

Hopping to help, good luck all. :)

---

### Post by danicyber on 2009-09-28
I have a FX1700m, which seems to allow me to use drivers <=180.44.
My linux is Ubuntu Jaunty, i installed the nvidia driver (190.13) to support Cuda 2.3, which crashed my machine badly. Back to the initial point, please let me know if you have any advices. 
Other problem: I'm a newbie, so I may be assuming somethings that are not true. Please, send comments.
thx, Dani

---

### Post by danicyber on 2009-09-29
Problem solved: tip = make sure older versions of your driver were completely removed from your system! nvidia uninstall will NOT do the job for you! Everything working fine:guitar:

---

### Post by spl on 2009-10-03
Didn't work for me with [NVIDIA Driver 190.18 Beta](http://developer.download.nvidia.com/compute/cuda/2_3/drivers/cudadriver_2.3_linux_32_190.18.run) because of mismatching version of the nvidia kernel module:
```

NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
NVRM: API mismatch: the client has the version 190.18, but
NVRM: this kernel module has the version 180.44.  Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.

```

Don't know if you guys use more recent kernel versions (mine is 2.6.28-15-generic).
Using older versions of the nvidia driver led to problems with the latest sdk.

My solution was to use nvidia drivers from nvidia-vdpau ppa repo:

```

sudo echo -e "deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main\ndeb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main" >> /etc/apt/sources.list.d/nvidia-vdpau_ppa.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767

```

Install:
nvidia-190-kernel-source
nvidia-190-libvdpau
nvidia-190-modaliases
nvidia-190-glx

(probably not all of the above packages are required, couldn't be bothered to do further testing...)

Possibly resulting conflicts:
libxine1-bin depends on nvidia-185-libvdpau
resolve by downgrading libxine1-bin

Restart gdm from terminal 1
```

sudo /etc/init.d/gdm restart

```

Download and install toolkit and sdk:
[CUDA Toolkit 2.3](http://developer.download.nvidia.com/compute/cuda/2_3/toolkit/cudatoolkit_2.3_linux_32_ubuntu9.04.run) (install with sudo)
[CUDA SDK 2.3](http://developer.download.nvidia.com/compute/cuda/2_3/sdk/cudasdk_2.3_linux.run) (install as user)

Update environment variables
```

echo "# CUDA stuff 
PATH=\$PATH:/usr/local/cuda/bin
LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:/usr/local/cuda/lib64
export PATH
export LD_LIBRARY_PATH" >> ~/.bashrc

```

Compile examples that come with sdk:
```

cd ~/NVIDIA_GPU_Computing_SDK/C/ #or wherever you had the installer put the files
make
cd bin/linux/release/

```

Fun things to run (in terms of eye candy): fluidsGL, particles, smokeParticles

Not tested on amd64, should work analogously though (download 64bit versions of toolkit and sdk at [http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html))

---

### Post by young.jeezy on 2009-10-05
Droogs, does anyone in this thread know what updates to avoid doing to not have the driver break?

I followed the steps in this thread, and am currently paranoid about doing updates because last year I did an update and my driver no longer worked. 

I am currently not updating anything since cuda is working. Is it really that bad to not update anything? Is there an easy way to disable the subset of updates that may break the nvidia driver that this thread installs? Thanks.

---

### Post by blakdogg on 2009-10-15
> **young.jeezy said:**
> Droogs, does anyone in this thread know what updates to avoid doing to not have the driver break?

I followed the steps in this thread, and am currently paranoid about doing updates because last year I did an update and my driver no longer worked. 

I am currently not updating anything since cuda is working. Is it really that bad to not update anything? Is there an easy way to disable the subset of updates that may break the nvidia driver that this thread installs? Thanks.
This is rubbish, installed CUDA for 9.04 and it killed it. Anyone know how I return to my working configuration ?

It seems I have to reinstall the old drivers, since I can run X with the gpl drivers but it goes wonky when I try to configure NVIDIA.

Thanks

---

### Post by blakdogg on 2009-10-15
> **blakdogg said:**
> This is rubbish, installed CUDA for 9.04 and it killed it. Anyone know how I return to my working configuration ?

It seems I have to reinstall the old drivers, since I can run X with the gpl drivers but it goes wonky when I try to configure NVIDIA.

Thanks
What do you know the CUDA driver has an "--uninstall"  that works.

---

### Post by aamir.nedian on 2009-12-17
I envy Aiyen on getting cuda up and running in first attempt! Here is my story though :(

I am running **64-bit Karmic (kernel version 2.6.31-16-generic)** on my workstation with Core i7 920 and GTX285. Before I installed the cuda driver "cudadriver_2.3_linux_64_190.18", my display along with Compiz effects were working flawlessly with the NVIDIA display driver that I was automatically asked to install right after installing Ubuntu. A day later, I installed the cuda driver, toolkit and sdk without any problems and even successfully compiled and run the devicequery example from SDK.

The problem is that now my gdm starts in low-graphics mode complaining that **[COLOR="Red"]"Failed to initialize the NVIDIA kernel module"[/COLOR]**. I searched for the error on many forums, but some people are suggesting to editing the config files that I don't even have. Somebody suggested to add ServerFlags section to xorg.conf but nothing has worked for me so far.
Section "ServerFlags"
    Option "IgnoreABI" "True"
EndSection

Please note that the installation of the driver was successful as I was able to compile and run devicequery example in the console mode. *It is only my display that is broken with the CUDA-driver*. To further prove my point and be sure of the source of error, I uninstalled the cuda driver and my display and compiz was again up and running even though I kept the new xorg.conf produced by the cuda driver installation. I am attaching the necessary logs and xorg.conf to help in troubleshooting. 

Please help me! Thanks in advance.

---

### Post by vitalstatistix on 2010-01-02
It looks to me like a lot of the problems people had here are due to not uninstalling the earlier nvidia drivers. Use envyng as a simple fix. Also whenever you install a driver through the terminal using the .run file it automatically compiles the nvidia kernel module. Also here is an excellent how to of the whole process:
[http://moelhave.dk/2009/12/nvidia-cuda-on-ubuntu-karmic-koala/](http://moelhave.dk/2009/12/nvidia-cuda-on-ubuntu-karmic-koala/)

I followed it for my current installation of cuda 3 beta with the nvidia driver 195.17 on karmic.

---

### Post by Aiyen on 2010-01-07
Hello again all. 

I noticed that I am not alone with the annoying ubuntu feature that every time there is a kernel update the Nvidia driver seems to go down. 

For some reason I have not yet figured out, it seems like every time it does a kernel update it screws up the xconf file with the nvidia settings in it. 

So far I have had no reason to change Nvidia driver version so I just reinstall the driver as I did the first time... and once it makes a new xconf file my system works again after a reboot. 

I would not be surprised if this does not work once you change nvidia driver version. But I am still in the phase where I want to work on cuda problems and not ubuntu for performance, so I am content with sticking with that driver version and no fuss every time there is a kernel update.

So for people who feel a similar way then my suggestion is to find a setting that works with as little fuss as possible and stick to it until you feel like you want to spend an evening solving yet another linux setting problem.

---

### Post by meborc on 2010-01-14
i will be going through the installation soon

machine - dell inspiron 1520 (geforce 8600M GT - 256M)
system - ubuntu 9.10 64bit
cuda 2.3

will let you know of my results

---

### Post by meborc on 2010-01-14
update ...

OK :D finally managed to get the matlab demo working with cuda

here are the steps that i took to get it working:

1 ) fresh install of ubuntu 9.10 64bit
2 ) sudo apt-get update && sudo apt-get dist-upgrade
3 ) add vdpau ppa for nvidia drivers
4 ) install nvidia 190 driver
5 ) install cuda toolkit and sdk (basically like poster no1)
6 ) install matlab to /home/$username/matlab
7 ) download matlab+cuda 1.1 from nvidia website
8 ) modify makefile to suit 64 bit + modify paths to respective locations

i kept getting errors on compilation in matlab... so i commented out this part from nvmex file ```
#    if [ "$compile_only" != "1" ]; then
#	if [ "$gateway_lang" = "C" ]; then
#	    files="$files $MATLAB/extern/src/mexversion.c"
#	else
#	    files="$files $MATLAB/extern/lib/$Arch/version4.o"
#	fi
#   fi
```

testing the FS_vortex file i got from 80 seconds with my dual2core T7250 @ 2.00GHz down to 20 seconds when my CPU was supported by my GPU :D

fun fun fun...

now to get CUDA and my fortran projects working...

---

### Post by wareagle on 2010-01-23
I solved my "low-graphics mode" problems by uninstalling not only the CUDA nVidia driver but also the nVidia kernel modules and binary driver from Synaptic (I just did a search for "nvidia" and removed "nvidia-180-kernel-source" and "nvidia-glx-180".

Also [this blog post]("http://www.herikstad.net/2009/04/setting-up-cuda-environment-in-ubuntu.html") may be helpful.  Specifically:

> 
A new error for Ubuntu Jaunty is that upon reboot you might get a message similar to:```

(EE)Failed to load module "type1" (module does not exist,0)
(EE)Failed to load module "freetype" (module does not exist,0)
(EE) NVIDIA(0) Failed to load the NVIDIA Kernel Module
(EE) NVIDIA ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.
```

To fix this problem edit the file /etc/modprobe.d/lrm-video and comment out the line install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS by putting a # in front of it.
Solution found from: [http://ubuntuforums.org/showthread.php?t=950777](http://ubuntuforums.org/showthread.php?t=950777)


---

### Post by meeas on 2010-01-28
If you have problems compiling, check to see if you have gcc-4.3 and g++-4.3 installed.  By default Ubuntu-9.04 installs version 4.4 of both files which prevents you from compiling cudasdk.

Once you get those packages installed, run the following commands to compile cudasdk:

cd ~/NVIDIA_GPU_Computing_SDK/C
make clean
sudo ln -fs /usr/bin/gcc-4.3 /usr/bin/gcc
sudo ln -fs /usr/bin/g++-4.3 /usr/bin/g++
make
sudo ln -fs /usr/bin/gcc-4.4 /usr/bin/gcc
sudo ln -fs /usr/bin/g++-4.4 /usr/bin/g++

Good luck!  ;-)

---

### Post by mercury80 on 2010-02-09
A little beginner talk here: After the instal I got this result:```
* Please make sure your PATH includes /usr/local/cuda/bin
* Please make sure your LD_LIBRARY_PATH
*   for 32-bit Linux distributions includes /usr/local/cuda/lib
*   for 64-bit Linux distributions includes /usr/local/cuda/lib64
* OR
*   for 32-bit Linux distributions add /usr/local/cuda/lib
*   for 64-bit Linux distributions add /usr/local/cuda/lib64
* to /etc/ld.so.conf and run ldconfig as root

* Please read the release notes in /usr/local/cuda/doc/

* To uninstall CUDA, delete /usr/local/cuda
* Installation Complete
```To do this, is it enough to do the following code?> **Aiyen said:**
> The next step is to add the necessary environment variables. In a terminal type in this. (Just type or copy it in one line at a time!)

```
echo "# CUDA stuff 
PATH=\$PATH:/usr/local/cuda/bin
LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:/usr/local/cuda/lib64
export PATH
export LD_LIBRARY_PATH" >> ~/.bashrc

```

Where does this code end up? Where can I see if I got it to the right place? (I did copy everything line for line.)

---

