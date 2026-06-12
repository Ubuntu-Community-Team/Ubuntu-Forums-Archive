---
title: "Feisty, Nvidia -  resolution lost after reboot"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Sale on 2007-04-30
I've installed the nvidia driver thru feisty restricted driver manager.

I can set the 1280x960_75 resolution while in gnome, using nvidia-settings command, but after I reboot or restart X, the resolution is lost and X defaults to 1024x768. The same thing happens when i use "sudo nvidia settings" and try to save the data I set to xorg.conf.

Here is what the nvidia settings writes to xorg.conf:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 160.0
    ModeLine       "1280x960_75.00" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x960_75 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0; 1280x960_75.00 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

the 
```
ModeLine       "1280x960_75.00" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync

```

Was added earlier, by me, as a result of using
```
~$ gtf 1280 960 75
```
Does anyone have any solution to this?

---

