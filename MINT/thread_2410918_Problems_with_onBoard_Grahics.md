---
title: "Problems with onBoard Grahics"
date: 2019-01-22
forum: MINT
---

### Post by Neill_R on 2019-01-22
Hello
 
I have found that the hardware I have has graphic problems running certain programs for example [https://stellarium.org/](https://stellarium.org/) where the on board graphics for the DELL OTIPLEX 780 MT [https://www.dell.com/downloads/global/products/optix/en/optiplex_780_tech_guidebook_en.pdf](https://www.dell.com/downloads/global/products/optix/en/optiplex_780_tech_guidebook_en.pdf) is not upto the job see below.


BEFORE considering Installing a VIDEO card I wish to extend my knowledge to see if there is a software solution first.

This is where I need your help and guidance please.



[SIZE=4]running Stellarium[/SIZE]

```

mint@mint:~$ stellarium
qt5ct: using qt5ct plugin
User config directory does not exist:  "/home/mint/.stellarium"
Creating directory  "/home/mint/.stellarium"
 -------------------------------------------------------
[ This is Stellarium 0.18.0 - http://www.stellarium.org ]
[ Copyright (C) 2000-2018 Fabien Chereau et al.         ]
 -------------------------------------------------------
Writing log file to: "/home/mint/.stellarium/log.txt"
File search paths:
  0 .  "/home/mint/.stellarium"
  1 .  "/usr/share/stellarium"
Config file  "/home/mint/.stellarium/config.ini"  does not exist. Copying the default file.
Config file is:  "/home/mint/.stellarium/config.ini"
Default surface format:  QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize -1, redBufferSize -1, greenBufferSize -1, blueBufferSize -1, alphaBufferSize -1, stencilBufferSize -1, samples -1, swapBehavior QSurfaceFormat::SwapBehavior(DefaultSwapBehavior), swapInterval 1, profile  QSurfaceFormat::OpenGLContextProfile(NoProfile))
Desired surface format:  QSurfaceFormat(version 2.1, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize 24, redBufferSize 8, greenBufferSize 8, blueBufferSize 8, alphaBufferSize 8, stencilBufferSize 8, samples -1, swapBehavior QSurfaceFormat::SwapBehavior(DefaultSwapBehavior), swapInterval 1, profile  QSurfaceFormat::OpenGLContextProfile(NoProfile))
StelGLWidget constructor
StelGraphicsScene constructor
initializeGL
OpenGL supported version:  "2.1 Mesa 18.0.0-rc5"
Current Format:  QSurfaceFormat(version 2.1, options QFlags<QSurfaceFormat::FormatOption>(DeprecatedFunctions), depthBufferSize 24, redBufferSize 8, greenBufferSize 8, blueBufferSize 8, alphaBufferSize 8, stencilBufferSize 8, samples 0, swapBehavior QSurfaceFormat::SwapBehavior(DefaultSwapBehavior), swapInterval 1, profile  QSurfaceFormat::OpenGLContextProfile(NoProfile))
StelMainView::init
Detected: OpenGL "2.1"
Driver version string: "2.1 Mesa 18.0.0-rc5"
GL vendor is "Intel Open Source Technology Center"
GL renderer is "Mesa DRI Intel(R) Q45/Q43 "
GL Shading Language version is "1.20"
MESA Version Number detected:  18
Mesa version is fine, we should not see a graphics problem.
[SIZE=4][B]GLSL Version Number detected:  1.2
This is not enough: we need GLSL1.30 or later.
You should update graphics drivers, graphics hardware, or use the --mesa-mode option.
Else, please try to use an older version like 0.12.5, and try there with --safe-mode
You can try to run in an unsupported degraded mode by ignoring the warning and continuing.
But more than likely problems will persist.[/B][/SIZE]
Segmentation fault (core dumped)
mint@mint:~$ 


```




```

[INDENT]mint@mint:~$ inxi -F
System:    Host: mint Kernel: 4.15.0-20-generic x86_64 bits: 64
           Desktop: Cinnamon 3.8.6  Distro: Linux Mint 19 Tara
Machine:   Device: desktop System: Dell product: OptiPlex 780 serial: N/A
           Mobo: Dell model: 0C27VV v: A01 serial: N/A
           BIOS: Dell v: A15 date: 08/06/2013
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           clock speeds: max: 2560 MHz 1: 2560 MHz 2: 2410 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.02hz
           OpenGL: renderer: Mesa DRI Intel Q45/Q43
           version: 2.1 Mesa 18.0.0-rc5
Audio:     Card Intel 82801JD/DO (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card-1: Intel 82567LM-3 Gigabit Network Connection driver: e1000e
           IF: enp0s25 state: down mac: b8:ac:6f:28:2f:16
           Card-2: Ralink RT2870/RT3070 Wireless Adapter driver: rt2800usb
           IF: wlx000f00407a61 state: N/A mac: N/A
Drives:    HDD Total Size: 15.5GB (97.1% used)
           ID-1: USB /dev/sda model: USB_FLASH_DRIVE size: 15.5GB
Partition: ID-1: / size: 1.9G used: 283M (15%) fs: overlay dev: N/A
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 37.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 184 Uptime: 1:02 Memory: 1600.2/3780.3MB
           Client: Shell (bash) inxi: 2.3.56 
mint@mint:~
[/INDENT]



```

---

### Post by Autodave on 2019-01-22
How much RAM does that machine have?  You are definitely low on specs with what is showing.  And the most video memory that that machine was built with was 256K which is quite low.  

Hopefully, someone will have some other help for you, for I think that you are just expecting too much from that machine.

---

### Post by Neill_R on 2019-01-22
> **Autodave said:**
> 

How much RAM does that machine have?  You are definitely low on specs with what is showing.  And the most video memory that that machine was built with was 256K which is quite low.  

Hopefully, someone will have some other help for you, for I think that you are just expecting too much from that machine


to answer your question using 2.1GiB of 3.7 GiB

---

### Post by Autodave on 2019-01-22
If it were my machine, I would be looking to add a graphics card.  You really don't need a gaming GPU, so I would imagine that you would probably be looking at about $50 - 70 US.

*Personally*, I like Nvidia cards since Nvidia drivers are readily available in the repositories.

---

### Post by Neill_R on 2019-01-22
> **Autodave said:**
> If it were my machine, I would be looking to add a graphics card.  You really don't need a gaming GPU, so I would imagine that you would probably be looking at about $50 - 70 US.

*Personally*, I like Nvidia cards since Nvidia drivers are readily available in the repositories.

I said "**BEFORE considering Installing a VIDEO card I wish to extend my knowledge to see if there is a software solution first. **"

 but thank you for responding

---

### Post by Autodave on 2019-01-23
I realize fully that you said that and I *did* say that I hoped that someone else would have better info for you.  And I still hope that they do.  But I doubt it.

---

### Post by Neill_R on 2019-01-23
I am hoping for guidance on how to try to perform the recommendations set out by the failed run of stellarium 
[SIZE=4]**This is not enough: we need GLSL1.30 or later.**[/SIZE]

---

### Post by Autodave on 2019-01-23
*golang-github-jtolds-gls-dev* is the closest that I have been able to find in the repositories.  I have no idea if that is what is needed or not.  Still researching.

Ahhhh.......*stellarium* is available in the repositories!  Is there a reason why you didn't you use that package instead of getting it elsewhere?  the GLS1.3 is evidently a dependency needed by the program to operate properly.  Any program in the repositories should automatically get the dependencies when it installs.  I would suggest that you try the one in the repositories.

---

### Post by Neill_R on 2019-01-23
[SIZE=4]**Linux Mint 19 i thought I did get it from the repositories sudo apt-get install stellarium but i will recheck **[/SIZE]

---

### Post by coffeecat on 2019-01-23
*Thread moved to the **Mint** subforum.*

And @Neill_R, please use the default font properties unless you wish to highlight a word or phrase. Using a large emboldened font for all or a large part of your post makes it look as though you are shouting.

---

### Post by Neill_R on 2019-01-23
CoffeeCat

I am slightly annoyed that you moved my post to a different forum. I remind you that Linux Mint 19 uses the Ubuntu 18.04 repositories so i am told. 

Now I have to re-enter all this again back in hardware forum. Because that is the issue. 

However I will reboot now in to Lubuntu 18.04 .

---

