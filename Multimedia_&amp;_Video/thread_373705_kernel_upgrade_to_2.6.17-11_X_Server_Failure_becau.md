---
title: "kernel upgrade to 2.6.17-11: X Server Failure because of Nvidia"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by golgaris on 2007-03-01
hi,

I'm running kubuntu 6.10 edgy and updated my kernel from version 2.6.17-10 (generic) to version 2.6.17-11 (generic). At the moment both kernels are installed.

On starting my computer with the older version (10) all is ok ...
The X server starts and I can work with my computer.

When I try to start the newer version (11), the X Server cannot be started, because of the restricted nvidia driver.
See the important parts of my Xorg.0.log output:

```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux golgari 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686

...

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "TwinView" "on"
(**) NVIDIA(0): Option "TwinViewOrientation" "LeftOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-81"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "56-75"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
[B](EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
[/B](II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Here the installed packages (dpkg-query -l | grep 2.6.17-)
```
ii  linux-headers-2.6.17-10                    2.6.17.1-10.34                       Header files related to Linux kernel version
ii  linux-headers-2.6.17-10-generic            2.6.17.1-10.34                       Linux kernel headers for version 2.6.17 on x
ii  linux-headers-2.6.17-11                    2.6.17.1-11.35                       Header files related to Linux kernel version
ii  linux-headers-2.6.17-11-generic            2.6.17.1-11.35                       Linux kernel headers for version 2.6.17 on x
rc  linux-image-2.6.17-10-386                  2.6.17.1-10.34                       Linux kernel image for version 2.6.17 on i38
ii  linux-image-2.6.17-10-generic              2.6.17.1-10.34                       Linux kernel image for version 2.6.17 on x86
**ii  linux-image-2.6.17-11-generic              2.6.17.1-11.35                       Linux kernel image for version 2.6.17 on x86**
rc  linux-restricted-modules-2.6.17-10-386     2.6.17.9-1                           Non-free Linux 2.6.17 modules on 386
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.9-1                           Non-free Linux 2.6.17 modules on x86_64 gene
**ii  linux-restricted-modules-2.6.17-11-generic 2.6.17.7-11.2                        Non-free Linux 2.6.17 modules on x86_64 gene**

```

and (dpkg-query -l | grep nvidia)

```
ii  nvidia-glx                                 1.0.9746+2.6.17.9-1                  NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                    NVIDIA binary kernel module common files
rc  nvidia-settings                            1.0-3ubuntu7                         Tool of configuring the NVIDIA graphics driv

```

Does anyone have a idea to fix this problem?

---

### Post by booe on 2007-03-02
This is your fix:
[http://ubuntuforums.org/showthread.php?t=374125](http://ubuntuforums.org/showthread.php?t=374125)

Please note what frodon said...

[quote=frodon]when you install nvidia drivers outside the repositories then you have to install them each time you update your kernel[/quote]

So every time you upgrade a package such as linux-restricted-modules, linux-kernel, etc, you will need to reinstall the NVIDIA proprietary drivers.

---

### Post by golgaris on 2007-03-02
I'm using ubuntu / kubuntu since version 5.10. I didn't need to install any drivers from external sources. The original ubuntu packages worked for me.

Thanks for help, I will try it.

---

### Post by golgaris on 2007-03-02
I tried to install the nvidia driver like it is described in that post.
There was no error on compiling, but the error is still here. With the same error message.

I'm doing the following things:
[LIST=1]
[*]boot the 2.6.17-11 kernel (where it doesn't work)
[*]execute the nvidia installer program (NVIDIA-Linux-x86-1.0-9746-pkg1.run, was downloaded before ...)
[*]License accept
[*]Recompile kernel module: yes
[*]Change config: No
[*]rebooting the computer
[*]same error ...
[/LIST]

Are there some packages that should be uninstalled?
Is it possible to have different kernel-modules installed (for the old kernel version). Maybe that one should be uninstalled ... (I need it for Internet research for this error ;-) )

---

### Post by golgaris on 2007-03-11
After reading many pages found in the internet I found the reason, why the installation did not work for me.

I installed the NVIDIA drivers in the way it was described in the declaration above. But it didn't work.

Here the resolution:
Open the file /etc/default/linux-restricted-modules-common and set the value nv for the variable DISABLED_MODULES.

After that you should run the NVIDIA driver installer once more.

After that the X server starts normally without problems ...

You should add this hint to the installation-description.

---

