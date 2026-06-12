---
title: "[LUCID LYNX] downgrade nvidia drivers"
date: 2010-05-03
forum: Multimedia Software
---

### Post by komasoftware on 2010-05-03
Hi,

From the XMBC and Boxee forums, it seems that past the Nvidia-185 driver multichannel PCM audio over HDMI is broken. Now when using the restricted drivers management from LUCID LYNX, I can only install the current version which is the 195 series.
Can somebody point me out how I can still install the 185 series drivers on my Acer Aspire REVO with NVIDIA ION.

thx!

Koen

---

### Post by komasoftware on 2010-05-03
I downloaded the install script of the 185 series from the nvidia site
wget [ftp://download.nvidia.com/XFree86/Linux-x86/185.19/NVIDIA-Linux-x86-185.19-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/185.19/NVIDIA-Linux-x86-185.19-pkg1.run)

Next I opened a terminal CTRL+ALT+F1 where I killed X

then I started the install script :

sudo sh ./NVIDIA-Linux-x86-185.19-pkg1.run -k $(uname -r) --x-module-path=/usr/lib/xorg/modules --x-library-path=/usr/lib

But failures all around... log attached.

Any experts out here ???

thx

---

### Post by Munk3y on 2010-05-03
I'm affected by this problem as well. I spent hours upon hours troubleshooting, updating, tweaking, testing to no avail. Finally I just went back to 9.10 and I'm good to go.

As far as I can figure out, the nVidia drivers are the problem and I can't find a way around it.

---

### Post by komasoftware on 2010-05-04
I didnt give up so easy and

* followed (among other) this guide : [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html) to build the nvidia drivers;
* I commented out a few lines in the sources that gave errors (in nv.c something with owner = THIS_MODULE and in os-agp.c something too)
* finally the whole nvidia installer process finished succesfully, building and installing the driver and creating a new X.org file

I rebooted but - **duh** - X wont boot, I ended up with this error log :

...........
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
dlopen: /usr/lib/xorg/modules/drivers/nvidia_drv.so: undefined symbol: resVgaShared
(EE) Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found


** Can somebody confirm wether it is possible or not to compile and run the 185.x series of the nvidia drivers on the 10.4 lucid lynx release ???**

Maybe this old release cannot be built against the kernel of lucid lynx {2.6.32-21-generic) ? Or how/where can I figure this out ??

thx

koen

---

