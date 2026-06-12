---
title: "problem on nvidia driver installation"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by sandro54 on 2008-03-28
Hi everybody
I have kubuntu 7.10 and a video card NVIDIA GeForce FX 5200. I tryed to install the driver NVIDIA using the following procedure by a text terminal (tty). I made the following:

download from NVIDIA repository the driver "NVIDIA-Linux-x86-169-12-pkg1.run"

sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install xserver-xorg-dev 

sudo /etc/init.d/kdm stop

sudo sh NVIDIA-Linux-x86-169-12-pkg1.run

the above operations ended with no error. So I edited the file xorg.conf an added "nvidia" under section_device and load "glx" under section_module, and the file /etc/default/.......-common where updated DISABLED_MODULES="nv".
At this point I restarted Xorg:  

sudo /etc/init.d/kdm start

but the machine is stopped (no GUI, screen blocked). I reboot the machine an I logged as 
root , so I typed :

start x

and I had on screen the following errors:
..........................................................................
FATAL : ERROR running install command for nvidia
nvidia: failed to load the nvidia kernel module
nvidia: ***aborting***
screen (s) found, but d'ont have an usable configuration
etc....
...................................................................
inside the log I founded the same errors :

nvidia: failed to load the nvidia kernel module
nvidia: ***aborting***
unload module "nvidia", "wfb", "fb"
screen (s) found, but d'ont have an usable configuration
etc.....
....................................................................

please have you some good  idea to help me   ???   thanks in advance.

Sandro

---

### Post by sandro54 on 2008-03-29
Hello  Guy,

I'm here to suffer but I don't go forward, could give me  a suggestion please .


kind regard
Sandro

---

