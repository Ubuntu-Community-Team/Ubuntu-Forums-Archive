---
title: "Nvidia Drivers For Intrepid Ibex (8.10)"
date: 2009-03-14
forum: Multimedia Software
---

### Post by jgeboski on 2009-03-14
Hi all,

I am trying to get my nvidia drivers installed in Ubuntu 8.10.  I have tried installing nvidia-glx-177 and installing it from the restricted drivers part of Ubuntu.  They supposedly install fine but, when I reboot all i get is Xserver not start up right.  So i uninstall the nvidia drivers reboot and Xserver will start up fine.  Any help would be greatly appreciated.

Thanks,
James

---

### Post by rlj1965 on 2009-03-14
> **jgeboski said:**
> Hi all,

I am trying to get my nvidia drivers installed in Ubuntu 8.10.  I have tried installing nvidia-glx-177 and installing it from the restricted drivers part of Ubuntu.  They supposedly install fine but, when I reboot all i get is Xserver not start up right.  So i uninstall the nvidia drivers reboot and Xserver will start up fine.  Any help would be greatly appreciated.

Thanks,
James

Have you tried Envy to install your driver? 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by red13 on 2009-03-15
What was the previous driver you had installed before installing the Nvidia 1.77 driver?

---

### Post by red13 on 2009-03-15
Seems the probloem is when xserver starts its not finding a legit video/graphics  card in xorg.conf, so try editing it so it will see what driver you want to use for xserver.
I would put example or howto but honestly I am not that smart but if you do a search on it you be able to find a solution.

---

### Post by romulus on 2009-03-15
I have been trying to figure this one out for months. Nobody seems to know why nvidia drivers are broken. (Geforce 8600GT) I've been going in circles trying to get 3D video drivers to work ever since 8.10 was in alpha. I search and search for solutions and now I am reduced to writing this post. PLEASE SOMEBODY HELP US!](*,)

---

### Post by norwoods on 2009-03-15
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then nclick Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

### Post by romulus on 2009-03-21
Kill me..Kill me now!](*,)](*,)](*,)](*,)

It didn't and still doesn't work. no 3d since 8.04

---

