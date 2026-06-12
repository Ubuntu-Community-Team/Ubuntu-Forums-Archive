---
title: "[SOLVED] Error: API mismatch: the NVIDIA kernel module has the version..."
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by shadowmint on 2007-12-26
I thought I'd post this here for anyone else who is having trouble. After getting a new 
graphics card and running the custom nvidia installer I got the following message 
when I tried to start X:

> Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but this X module has the version 1.0-9631. Please make sure that the kernel module and all NVIDIA driver components have the same version.

After a lot of trouble it turns out the problem is directly related to what kernel modules are 
around. Specifically, the wrong version of some kernel modules seems to been left there.

To solve this: 

1) Start a generic xserver. This can be done (usually) by editing /etc/X11/xorg.conf and 
changing the block that reads something like:

> Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection


to:

> Section "Device"
    Identifier     "Generic Video Card"
    Driver         "vesa"
EndSection


This should let you start a generic vesa video device. 


2) Remove the restricted drivers for the system, specifically any of these drivers:
nvidia-glx nvidia-glx-legacy nvidia-glx-new linux-restricted-modules-* nvidia-glx 

To do this run synaptic (if you manage to get X working you can do this as root as: 
X&; export DISPLAY=:0; synaptic)

Search for nvidia and remove any installed packages. Search for the packages 
listed adobe specifically and remove all of these.


3) Check that the modules are ACTUALLY gone. Run: modprobe -l |grep nvidia
There should be no files. If there are any entries, eg:
/lib/modules/2.6.20-16-generic/kernel/drivers/video/nvidia.ko

Then create a backup folder somewhere and move that module to the backup
folder. Then run: modprobe -r [NAME] and repeat. You should eventually get
no response to 'modprobe -l |grep nvidia' and if you type: 'modprobe nvdia'
the response should be: FATAL: Module nvidia not found.


4) Close the X server if you're running one, and run the nvidia installer:
sh NVIDIA-Linux-x86-96.43.01-pkg1.run or whatever. 

Nb. When I did this the installer actually reported a few errors; failed to 
install various files, but it did -correctly- install the one important file:
nvidia.ko in the modules directory.



**This is the direct way of doing this, and may mess up package deps.**
However, it should get rid of any existing nvidia modules which are causing
the conflict message.

Hope it helps!


**Edit:** Running the command: 'dkpg-reconfigure xserver-xorg' will fix your
xorg.conf if you mess it up, but it won't fix the API mismatch no matter how many
times you do it or get told to do it... :P

---

### Post by pingpongboss on 2008-05-18
holy cow thanks! this fixed my problem perfectly. THanks for posting your solution :guitar:

---

