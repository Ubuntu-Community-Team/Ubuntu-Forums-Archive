---
title: "Trouble installing nvidia mx200 driver, x will not load"
date: 2010-12-31
forum: Multimedia Software
---

### Post by Aisteru on 2010-12-31
I am trying to setup a computer with xubuntu 10.10 for my dad. It is mostly working, but flash animations/games run somewhat poorly. I think I might be able to fix this by using the non-free nvidia drivers, but I cannot seem to get them installed.

Sysinfo reports that the video card is an nvidia geforce mx200, so I downloaded the nvidia 96 driver package from the repositories, ran the configuration program, & rebooted. As you may guess, x did not load. 

I have been working on this intermittently for a few weeks, & I do not remember everything I might have tried to fix it, but here is what I am sure of:

Sysinfo reports that the video card is an nvidia geforce mx200

when i try "sudo modprobe nvidia," I get the message "FATAL: Module nvidia not found."
"sudo modprobe nvidia-96" gives no such error.

When I check the Xorg.0.log, I find:

[    19.283] (II) LoadModule: "nvidia"
[    19.283] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.383] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData
[    19.384] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.384] (II) UnloadModule: "nvidia"
[    19.384] (EE) Failed to load module "nvidia" (loader failed, 7)
[    19.384] (EE) No drivers available.
[    19.384] 
Fatal server error:
[    19.384] no screens found

The nouveau driver does not seem to work either, but if I remove the xorg.conf file, x works okay.

I should say, if I can get this working, it would help ween my folks off their Windows dependency. :oD

I will be glad to post anything I can to help diagnose the problem. Any advice on how to get Flashplayer running more smoothly would also be appreciated.

---

### Post by marl30 on 2010-12-31
> **Aisteru said:**
> I am trying to setup a computer with xubuntu 10.10 for my dad. It is mostly working, but flash animations/games run somewhat poorly. I think I might be able to fix this by using the non-free nvidia drivers, but I cannot seem to get them installed.

Sysinfo reports that the video card is an nvidia geforce mx200, so I downloaded the nvidia 96 driver package from the repositories, ran the configuration program, & rebooted. As you may guess, x did not load. 

I have been working on this intermittently for a few weeks, & I do not remember everything I might have tried to fix it, but here is what I am sure of:

Sysinfo reports that the video card is an nvidia geforce mx200

when i try "sudo ," I get the message "FATAL: Module nvidia not found."
"sudo modprobe nvidia-96" gives no such error.

When I check the Xorg.0.log, I find:

[    19.283] (II) LoadModule: "nvidia"
[    19.283] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.383] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData
[    19.384] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.384] (II) UnloadModule: "nvidia"
[    19.384] (EE) Failed to load module "nvidia" (loader failed, 7)
[    19.384] (EE) No drivers available.
[    19.384] 
Fatal server error:
[    19.384] no screens found

The nouveau driver does not seem to work either, but if I remove the xorg.conf file, x works okay.

I should say, if I can get this working, it would help ween my folks off their Windows dependency. :oD

I will be glad to post anything I can to help diagnose the problem. Any advice on how to get Flashplayer running more smoothly would also be appreciated.

I introduced someone to Ubuntu 10.10, who has an old Nvidia mx400. It installed and ran, but the Nvidia driver would not install, so the computer had no 3d acceleration enabled. I switched him to Linux Mint 9. After installing it, it popped and asked me if I wanted to install the Nvidia driver. It installed the 96 version driver. 3d acceleration was enabled, and compiz settings could now work. Linux Mint 9 seems to have better support for older hardware than Ubuntu. 

If it use the 96 drivers, Linux mint may work.

---

### Post by Aisteru on 2010-12-31
Thanks for the suggestion. I looked into Mint briefly a while back, but  the memory requirement scared me off. I think the one I am working on  now has enough, though. I might try Mint, if I can not get the driver working  after waiting for a few more suggestions. I would do it now, but I hate  to start over after taking the trouble to get everything setup. I  can image the HD, then restore it if Mint does not help, but if it  would still mean starting over if it does work.
 
 Anyway, thanks a lot.

---

### Post by Aisteru on 2011-01-13
bump!!

---

### Post by mfu on 2011-01-15
Hello, 

I did the upgrade from 10.04 to 10.10 on an old PC with a GeForce MX200. And went through the same issue.

Basically, Ubuntu 10.10 introduce a new Xorg server, that cannot load the nvidia96 driver.

The solution I used : downgrade the xorg server.

The general "how-to":
  uninstall xorg and associate
  change version from maverick to lucid in atp/sources.list
  install xorg and associate
  change back version in atp/souces.list

I got the details in the forums.

Be aware, you get a final system that is a mix between old and new ! Update and upgrade become less that easy. For the rest, works fine.

Good Luck,

M'Fu

---

### Post by Aisteru on 2011-01-21
Well, this is a bitter pill. I am thankful for the advice, but this  system is for my Window$ addict dad. Since he is an Esperantist, the  fact that Ubuntu is more Esperanto friendly is a good selling point, but  not being able to use Flash well is detracts quite a bit from the  appeal. I have read that the Linux version of Flashplayer does not get  any benefit from hardware acceleration. I don't know whether that is  true, but if it is, this is an exercise in futility.

On another note, I tried installing the driver from the Nvidia website,  but to no avail. The only difference now is that the error says:

[    18.376] (II) LoadModule: "nvidia"
[    18.376] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    18.378] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.378]     compiled for 4.0.2, module version = 1.0.0
[    18.378]     Module class: X.Org Video Driver
[    18.378] (II) NVIDIA dlloader X Driver  96.43.19  Wed Oct 27 19:07:40 PDT 2010
[    18.378] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    18.380] (--) using VT number 8

[    18.393] (II) Loading sub module "fb"
[    18.393] (II) LoadModule: "fb"
[    18.394] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.395] (II) Module fb: vendor="X.Org Foundation"
[    18.395]     compiled for 1.9.0, module version = 1.0.0
[    18.395]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.395] (II) Loading sub module "ramdac"
[    18.395] (II) LoadModule: "ramdac"
[    18.395] (II) Module "ramdac" already built-in
[    18.395] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    18.395] (==) NVIDIA(0): RGB weight 888
[    18.395] (==) NVIDIA(0): Default visual is TrueColor
[    18.401] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.401] (**) NVIDIA(0): Enabling RENDER acceleration
[    18.401] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    18.401] (II) NVIDIA(0):     enabled.
[    18.402] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
[    18.402] (EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
[    18.402] (EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
[    18.402] (EE) NVIDIA(0):     Please consult the NVIDIA README for details.
[    18.402] (EE) NVIDIA(0):  *** Aborting ***
[    18.402] (II) UnloadModule: "nvidia"
[    18.402] (II) UnloadModule: "fb"
[    18.402] (EE) Screen(s) found, but none have a usable configuration.
[    18.402] 
Fatal server error:
[    18.402] no screens found

At least the module seems to be there now, but I guess this card may not  be supported by the driver, or the server, as mfu said. (Sigh) I think  I'll go listen to Superchic[k] & cry now. JK

---

### Post by Aisteru on 2011-01-24
Huzzah!! :D I fixed it! Rather than installing the older version of Xorg, I installed the newer driver from the proposed updates. I went to synaptic,  went to the Settings menu > Repositories > Updates, & there checked the box for the Pre-released updates. I then reloaded the package info, & installed everything I thought I might need, ran "sudo nvidia-xconfig," rebooted, held my breath, etc. 

It worked! Flashplayer still doesn't work as well as I would like, but it seems to work a bit better anyway.

Weirdly, I still can't find the nvidia module using modprobe, but the the xorg.conf I have seems to be set to load the driver.

---

