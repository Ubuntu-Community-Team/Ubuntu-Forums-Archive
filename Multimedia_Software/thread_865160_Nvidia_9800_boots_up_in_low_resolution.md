---
title: "Nvidia 9800 boots up in low resolution"
date: 2008-07-20
forum: Multimedia Software
---

### Post by elias832 on 2008-07-20
Hi,

I have installed the nvidia driver from the nvidia website version NVIDIA-Linux-x86_64-173.14.09-pkg2.run.

I have installed all the required libraries to complete the installation.
I stop the X server, then log in as a level 3, install the driver, it tells me that there are no precompiled kernels for nvidia, it tries to go online and get the kernel but it fails, after that it installs the driver.
Everything goes smoothley, at it tells me that the driver has been successfully installed, so I startx, i see the nvidia splash screen, and i log in, everything works normally, resolution 1600x1200, the compiz desktop effects work... BUT after i reboot, my screen goes back to 800x600 and it will not change it. Once i launch the nvidia X server settings, it tells me to run nvidia-xconfig as a root. I do that, and launch it again, i get the same message. I cannot change the resolution more than 800x600.
In the Hardware drivers, there are no drivers listed.
I run Ubuntu 8.04
Nvidia 9800 512MB

when i run lspci -n | grep 0300:
02:00.0 0300: 10de:0612 (rev a2)
Any help is appreciated. Thank you.

---

### Post by overdrank on 2008-07-20
> **elias832 said:**
> Hi,

I have installed the nvidia driver from the nvidia website version NVIDIA-Linux-x86_64-173.14.09-pkg2.run.

I have installed all the required libraries to complete the installation.
I stop the X server, then log in as a level 3, install the driver, it tells me that there are no precompiled kernels for nvidia, it tries to go online and get the kernel but it fails, after that it installs the driver.
Everything goes smoothley, at it tells me that the driver has been successfully installed, so I startx, i see the nvidia splash screen, and i log in, everything works normally, resolution 1600x1200, the compiz desktop effects work... BUT after i reboot, my screen goes back to 800x600 and it will not change it. Once i launch the nvidia X server settings, it tells me to run nvidia-xconfig as a root. I do that, and launch it again, i get the same message. I cannot change the resolution more than 800x600.
In the Hardware drivers, there are no drivers listed.
I run Ubuntu 8.04
Nvidia 9800 512MB

when i run lspci -n | grep 0300:
02:00.0 0300: 10de:0612 (rev a2)
Any help is appreciated. Thank you.

Hi and welcome, this is the beginners team forum and the support questions should be asked in the beginners forum
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)
But as for your issue you may look here
[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

---

