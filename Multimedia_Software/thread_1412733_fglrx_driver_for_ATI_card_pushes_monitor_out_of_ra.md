---
title: "fglrx driver for ATI card pushes monitor out of range"
date: 2010-02-21
forum: Multimedia Software
---

### Post by KingofthePlebs on 2010-02-21
**fglrx driver for ATI card pushes monitor out of range** 			
 			 			 		   		 		 		Hey guys, this is my first post in the community, as I just installed Ubuntu 9.10 for the first time this weekend. I am certainly no computer expert, but I'm hoping that through learning to use and utilize Ubuntu my knowledge will increase.

I am running Ubuntu 9.10, my video card is ATI Radeon HD 3600

Heres my issue:

When I originally attempted to enable desktop effects, I was told that I was unable to do so. Not being one to rush to ask a question, I tried to figure out the issue, and it seemed to be that I needed to install the fglrx driver available for ATI cards- a simple enough fix. I installed the driver, and rebooted my machine, and everything seemed to be fine- the initial splash page came up- but immediately afterwards (presumably when I reached the login screen) My monitor went out of range. 

Not being strong in coding, I was unable to figure out a way to remove the driver without a GUI (though I think I very well could have), so I had to uninstall and reinstall (no sweat, I hadn't really started anything yet). However, its obvious that the fglrx driver is what blew it out of range.

My question is, is there anything I can do to get this driver to work on my machine? I found similar questions but they all seemed either to be slightly different from my issue or recommended changing the .xorg file, which does not exist in 9.10. Please help, thanks in advance! ):P

---

### Post by Voorhees1979 on 2010-02-21
I have had this before. I think your xorg.conf has a higher screen res set to what your monitor can handle. So goto /etc/X11 and edit xorg.conf as su. Look at the file and change all the screen res settings to the exact screen res of your monitor. Backup xorg.conf first so you can always put it back.

Hope this is the answer.

Cheers

---

### Post by KingofthePlebs on 2010-02-21
Thanks for the response, but I was under the impression that 9.10 was lacking an xorg.conf file, am I wrong about that?

---

### Post by crunch256 on 2010-02-21
xorg.conf is not required (or included by default) anymore, but you can still use one. Just create the file in /etc/X11

I have the same problem. Had to piece together the config file using the monitor manufacturer's specs. It got me the resolutions/refresh rates I wanted with the *radeon* driver.

Unfortunately, xorg.conf did not solve my problem with the fglrx driver... still pushes the monitor out of range after I install it.

---

### Post by KingofthePlebs on 2010-02-21
So how did you go about piecing it together?

---

### Post by crunch256 on 2010-02-22
I wasn't too sure about my monitor's specs, so I started off just piecing together parts of other ppl's xorg.conf files that I found in forums. I used gtf (CLI program) to generate the modelines I couldn't find. After a bit, I used some xorg.conf tutorials to clean up my file and set some of the optional parameters.

Then, I found a copy of my monitor's manual online, and used the [XFree86 Modeline Generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") to calculate more modelines based on more complete info.

Also...
I'm not really sure how to check the vendor and model names that the monitor reports to Ubuntu, so I just put descriptive info.

Here's what I've been using:

```
Section "Monitor"
    Identifier    "Proview 786N"
    VendorName    "Proview Electronics"
    ModelName    "PS720F-1s"
    HorizSync    30 - 70
    VertRefresh    50 - 160

    # Monitor's recognized display modes
        Modeline        "800x600_85" 58.20 800 832 1048 1080 600 611 620 631  -HSync +Vsync
        Modeline        "800x600_100" 71.71 800 832 1104 1136 600 610 620 631  -HSync +Vsync
        Modeline        "1024x768_75" 85.52 1024 1056 1376 1408 768 782 792 807  -HSync +Vsync
        Modeline        "1024x768_85" 100.94 1024 1056 1432 1464 768 782 793 807  -HSync +Vsync

    # Other valid display modes
        Modeline        "1152x864_70" 101.90 1152 1184 1568 1600 864 881 891 908  -HSync +Vsync
        Modeline        "1152x864_74" 109.72 1152 1184 1600 1632 864 880 891 908  -HSync +Vsync
        Modeline        "1280x960_60" 105.68 1280 1312 1712 1744 960 979 989 1009  -HSync +Vsync

    Option        "DPMS" "true"
    Option        "PreferredMode" "1024x768_85"
    Option        "TargetRefresh" "85"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Device        "ATI Radeon HD 4200"
    Monitor        "Proview 786N"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "ATI Radeon HD 4200"
    Driver    "radeon"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

```

---

### Post by crunch256 on 2010-02-22
My immediate concern was to get a decent refresh rate. After I got my modelines right, I tried using fglrx again, but the display was still out of range.

It looks like the xorg.conf fixed the problem with fglrx for [some people]("http://ubuntuforums.org/showthread.php?t=379736") (check out the Edit at the bottom of the 1st post).

---

### Post by crunch256 on 2010-02-22
Finally got mine working with fglrx.


[LIST=1]
[*]Let the ATI suite generate/modify xorg.conf:
**sudo aticonfig --initial**
[*]Edit the xorg.conf so that **my monitor section** is used (and deleted any redundant sections)
[*]Rebooted and hoped for the best
[*]Display was good(!!), so launched the ATI management console:
sudo amdcccle
[*]Fired up Extreme Tux Racer to verify 3d acceleration.
[/LIST]

Hope that helps

---

### Post by fedraljack on 2010-02-22
Both the X.org Intel drivers and DRI driver and libraries can be compiled out-of-tree and be usable.I have done that before when trying out different features that are only avialable via cvs.Remember almost all of it, except for the DRM or AGP stuff, is userspace.

---

### Post by KingofthePlebs on 2010-02-24
Thanks for all the help guys, I'll try this out when I get the chance this weekend

---

