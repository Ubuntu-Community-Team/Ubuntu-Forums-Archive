---
title: "can't install the nvidia drivers"
date: 2009-02-03
forum: Multimedia Software
---

### Post by sethedge on 2009-02-03
Hi everybody.

I tried to install the nvidia drivers, in order to use them instead of the vesa ones...

Here is what happens when I use sudo apt-get install nvidia-glx-180:

> (Reading database ... 155572 files and directories currently installed.)
Preparing to replace nvidia-180-kernel-source 180.11-0ubuntu1~intrepid1 (using .../nvidia-180-kernel-source_180.11-0ubuntu1~intrepid1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-180-kernel-source ...
Setting up nvidia-180-kernel-source (180.11-0ubuntu1~intrepid1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 180.11
Doing initial module build

Error! Your kernel source for kernel 2.6.24-23-generic cannot be found at
/lib/modules/2.6.24-23-generic/build or /lib/modules/2.6.24-23-generic/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.24-23-generic (x86_64) first.
Done.


Any clue?

---

### Post by jstarek on 2009-02-04
I just had the exact same problem. I should first mention that my system environment may be a bit unusual because I have a 2.6.27-11-server kernel with the ubuntu-desktop metapackage added on top of it (for workstation use).

I looked into the details of this problem and summarized my findings on [Bug 325274]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/325274") . As you can see, I did not really get down to the source of the problem but found a workaround. In short, install module-assistant, your kernel headers and sources and use module-assistant's installation routine by invoking 

```
sudo module-assistant auto-install nvidia
```

That seems to set the missing symlink, and I got the driver working that way.

---

### Post by sethedge on 2009-02-04
perfect! thanks a lot!!!
no more error from apt-get...
just now, when launching "startx", it gets stuck, and here is the tail of the xorg log file:

> (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


I swear I have an nVidia card, see this output of lspci:
> $ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

Any clue?

---

### Post by MrCharles on 2009-02-05
[http://ubuntuforums.org/showthread.php?t=1054842](http://ubuntuforums.org/showthread.php?t=1054842)

---

