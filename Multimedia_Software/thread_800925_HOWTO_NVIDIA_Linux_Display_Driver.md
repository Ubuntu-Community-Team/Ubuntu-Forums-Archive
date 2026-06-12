---
title: "HOWTO: NVIDIA Linux Display Driver"
date: 2008-05-20
forum: Multimedia Software
---

### Post by gmerrick on 2008-05-20
HOWTO: Install Proprietary Nvidia Linux Drivers for 

I found that alot of the other howto's were kind of vague, so here is something that works quite well for me.

Download from the nvidia web site the latest linux pkg for the video card you are using
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

The one I am using is NVIDIA-Linux-x86-169.12.pkg1.run from

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)

Ensure that your system is up to date by running 
    sudo apt-get update


Ensure that build-essential, make, gcc, linux headers (for your kernel version), pkg-config, xserver-xorg-dev, linux-libc-dev, libc6 are installed using apt-get or synaptic (do a search for the package names)

Uninstall via apt-get &#8211;purge nvidia-glx

Delete /etc/init.d/nvidia-glx
       /etc/init.d/nvidia-kernel 
       /lib/linux-restricted-modules/.nvidia_new_installed


Add in using your favourite editor 
sudo nano /etc/default/linux-restricted-modules-common
 the following:

DISABLED_ MODULES= &#8220;nv, nvidia-new&#8221;

Crtl-alt F1 into a text window and log in to your account

shutdown gdm by sudo /etc/init.d/gdm stop

as fakeroot or sudo run  NVIDIA-Linux-x86-169.12.pkg1.run ,and select the default setting and allow the package to build a new kernel module and configure Xorg automatically.

sudo ./NVIDIA-Linux-x86-169.12.pkg1.run

This has worked well for me in 7.10 and 8.04 where I need to get 30" 2650x1600 screens working as the build in drivers cannot handle the screens.

restart gdm by 
sudo /etc/init.d/gdm start

---

### Post by Mortosa on 2008-05-20
Glad to see this. I did it and it worked for me. I am curious however to see why it doesnt say what my model of video card is. It only says nvidia. Normally in the past it would say "NVidia 9600GT" for example.

---

### Post by gmerrick on 2008-05-20
I added the removal of the file

  /lib/linux-restricted-modules/.nvidia_new_installed

somehow missed that in my notes....you may want to go and remove that or leave as is.

I complied this from trial and error and notes included with the Nvidia driver, which I can't locate anymore.

---

### Post by Mortosa on 2008-05-20
Thanks I will try that when i get home from work.

---

