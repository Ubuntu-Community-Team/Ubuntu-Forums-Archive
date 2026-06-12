---
title: "NVidia 9629 X problems"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by machs_fuel42 on 2006-11-27
i recently upgraded to NVIDIA-Linux-x86-1.0-9629 after an ubuntu upgrade left me w/o an working X server.  this works - however i need to install it every time that i reboot since X will crash before i get to the login screen

what i did to install: 
$sudo ./NVIDIA-Linux-x86-1.0-9629-pkg1.run
$ startx

this is a bit of a pain.. i'm not to sure whats causing X to crash. 

here is a snipnet from my Xorg.0.log

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "false"
(**) NVIDIA(0): Option "MetaModes" "1280x1024;1024x768;800x600;640x480;512x384"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

also tryed

```
$lsmod | grep nv
nvidia               3924156  0 
agpgart                37072  2 nvidia,via_agp

```

so it looks to me like the nvidia driver is being loaded at boot...

at the advice of the readme file i compiled the nvidia driver for my k7 kernel... same problem on reboot

Can anyone lend me some advice?

thanks -

---

### Post by tseliot on 2006-11-28
What's the model of your card?

---

### Post by machs_fuel42 on 2006-11-28
GeForce4 Ti 4200 AGP 8x

also glxinfo and glxgears causes segmentation faults

---

