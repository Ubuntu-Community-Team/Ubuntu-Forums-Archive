---
title: "Unable to install Nvidia driver on 9500M"
date: 2008-05-23
forum: Multimedia Software
---

### Post by jesper_wilhelmsson on 2008-05-23
Hi,
I recently bought an Asus G1SN-AK023C that has a GeForce 9500M GS.
The first thing I did was of course to install Ubuntu 8.04 on it (the preinstalled Windows never knew what hit it :) )

The Nvidia drivers that comes with Ubuntu did not recognize the card, which is quite understandable since it is a fairly new card. I went to Nvidia to download a new driver and found [driver version 173.08]("http://www.nvidia.com/object/linux_display_amd64_173.08.html") that supports my card.

I have tried both the 64-bit driver on a 64-bit version of Ubuntu, and the 32-bit driver on a 32-bit Ubuntu. The hardware is 64-bit so I'd prefer to get the 64-bit version to work.

Unfortunately I can not get the driver to install properly. After having compiled it complains that it can not load the kernel module nvidia.ko.
According to the error message:
"This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s)."

I have followed the steps in [this thread in Nvidias forum]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") to ensure that I have the required packages and that no old nvidia stuff is present.

In the /var/log/nvidia-installer.log I read the following:
Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko': -1 No such device

I interpret this as the driver did not compile properly, or maybe it just ended up somewhere else..?

There is no directory /usr/src/nv, but of course I don't know where the installer has found its working directory. Maybe the '.' is somewhere else..?
A 'find / -name nvidia.ko' finds nothing.

What does the error message mean with "improperly configured kernel sources"? I just installed the package linux-source using apt-get and did no configuring what so ever. (I've got the linux-headers as well and some other misc packages.)

I can see in the logfile that there are compiler warnings about using void* in arithmetics (ouch, why do they do that?!) but in the end it claims to have compiled it successfully. I don't know how to access the source so I can't do anything about that currently.

Does anyone have a similar experience, a solution, any help or advice? I'm stuck and it would be a pitty to be forced to install Windows on this machine since I bought this particular hardware because it was supposed to work well with Ubuntu.

---

### Post by fsckedagain on 2008-05-23
Did you install the lib-dev package?

That is required to compile the kernel module when you try to install the driver.


editted to welcome our new friend :)

---

### Post by jesper_wilhelmsson on 2008-05-23
I can not find any package called lib-dev. I searched for 'lib-dev' in Synaptic and found a bunch of packages called lib'something'-dev, but none that was called just lib-dev or anything that lead me to think about kernel modules.
I do have a few other dev-packages installed though. linux-libc-dev and linux-kernel-devel are among them. The second one was installed in desperation when I thought I had tried everything else, but it didn't help... :(

---

### Post by hotweiss on 2008-05-25
Just use Envy, the 169.12 drivers work with that video card; I have an Asus notebook with that same video card.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jesper_wilhelmsson on 2008-05-25
The problem seems to be the RAM. I have 3GB in there and that is too much for the poor driver :)  Removig 1GB made the driver work.
The driver is still beta so hopefully this will be fixed. Once the driver goes final, how long time should one expect to wait before the new driver is included in Ubuntu?

---

### Post by add2700 on 2008-07-07
Check out the fix posted here:

[http://ubuntuforums.org/showpost.php?p=5331990&postcount=11](http://ubuntuforums.org/showpost.php?p=5331990&postcount=11)

I took it from the nvnews.net forums and it worked for me.

---

