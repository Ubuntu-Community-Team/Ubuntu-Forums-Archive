---
title: "Cannot use NVIDIA driver in Kubuntu 10.10"
date: 2011-09-08
forum: Multimedia Software
---

### Post by lparsons42 on 2011-09-08
I have a Thinkpad T510 with an Nvidia NVS3100M discrete graphics card, and I am not able to use the Nvidia driver for it in Kubuntu 10.10.  I was able to install the driver through Applications->System->Additional Drivers however when I try to boot with the drivers enabled, Xorg will not start.  Any attempt to run X with the nvidia drivers enabled through /etc/X11/xorg.conf results in a failure to start X.  The last messages from xorg are as follows:
```

[    71.569] (II) LoadModule: "nvidia"
[    71.570] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    71.570] (II) Module nvidia: vendor="NVIDIA Corporation"
[    71.570]    compiled for 4.0.2, module version = 1.0.0
[    71.570]    Module class: X.Org Video Driver
[    71.570] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    71.570] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    71.570] (--) using VT number 7

[    71.573] (EE) No devices detected.
[    71.573] 
Fatal server error:
[    71.573] no screens found
[    71.573] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[    71.573] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    71.573] 

```

I read an [URL="http://http://ubuntuforums.org/showthread.php?t=901696"]
older thread from someone with a similar problem[/URL], however dpkg-reconfigure made no difference in my case.

I originally ran the regular open source drivers on this system, however I recently encountered an application where opengl and accelerated 3D is valuable so I wanted to get the nvidia drivers working.  

I have also found that opengl is not working correctly when I am running the open source drivers (as reported by kinfocenter).  If I try to run glxgears, the following error is returned:```
glxgears 
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

I'm not real sure what to do now.  I am trying to download the latest drivers directly from nvidia at this point, in case they may be slightly newer than what kubuntu will install on its own.  I suspect I need to reinstall opengl and its associated bits (glx, mesa, dri, ...) though I can't seem to get the graphic package manager to do that.

---

### Post by lparsons42 on 2011-09-08
I think I may have found a solution to this problem already.  The thread here on the T410 thinkpad with the nvidia graphics mentions that you can switch your graphics card in the BIOS, as these systems essentially have two graphics chipsets (both an Intel and an nvidia).  Some OSes (probably only ones from Microsoft, I suspect) support switching graphics chips on the fly (as in, after booting).  

So I went into my BIOS and set it to run only the nvidia chip.  Now my system comes up, runs the nvidia chip, and opengl seems happy.  Rather frustrating that I had to go through this, but things look good now.  I guess switching on the fly is useful for some road warriors however I intend to use the living daylights out of my graphics chip (for work, not for games) so I don't gain much by way of a mechanism to switch between them.

---

### Post by lparsons42 on 2011-09-09
I just wanted to add that I found a solution to the inability to adjust brightness on my system:
[enable nvidia brightness control in ubuntu 10.04]("http://andresclari.com/blog/enable-nvidia-brightness-control-in-ubuntu-10-04/") which basically boils down to adding the line ```
Option "RegistryDwords" "EnableBrightnessControl=1"
``` to the DEVICE section of your /etc/X11/xorg.conf file.  I did that, rebooted, and life is great now.  
Hence it seems all we needed was one switch that was mysteriously set to "off" for Xorg.  Once we set it to on, we're back in business.
This was on my Thinkpad T510, core i5, with nvidia NVS3100M graphics card in Kubuntu 10.10.  I suspect anyone running any recent Xorg distribution on a system with an nvidia graphics card would find this should work; likely other laptop users will find it more useful than desktop users.

---

