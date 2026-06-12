---
title: "Monitor bad resolution with nouveau driver"
date: 2010-09-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by oasick on 2010-09-15
I have a Philips 220cw9fb monitor and since I updated the system on Monday 13 the display has a bad resolution. 
The right resolution of the monitor is 1680x1050 (16:10) but now the bottom and right side are cut off.
I can fix manually the session with de gnome display tool, but gdm still appears cut and I can not see the options bar appears below.
I tried to repair the X using the tools of system startup too and have partially repaired because it looks good using the driver "fbdev", but with this driver I can't see videos or TV.
Does anyone have a similar problem?
Thanks!

---

### Post by cariboo on 2010-09-15
I would help a lot if you told what make/model of video card you are using.

---

### Post by Yumi on 2010-09-15
I observerd a similar behaviour with my monitor which should display a resolution of 1920x1080. First nouveau did that naturally. Recently it showed windows "hanging of the screen". I think the problem is in the xorg.conf file. This is too rudamentary after the automatic configuration by maverick. The graphic card nor the monitor where recognised by nouveau.

My solution is to switch to the new nvidia 256. driver and all is well. Here the relevant section of my xorg.conf just for reference.

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2250 SERIES"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1920x1080_60_0 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by MacUntu on 2010-09-16
Maybe it's the wrong refresh rate rather than the wrong resolution? I've seen something similar with recent updates and nvidia-current. I now have to have the "metamode" in the xorg.conf or X will start with 60 Hz. So maybe you just need to add the right modeline to your xorg.conf.

My nouveau xorg.conf looks like this:

```
Section "ServerLayout"
    Identifier      "Layout0"
    Screen          "Screen0"
EndSection

Section "ServerFlags"
    Option          "Dontzap"   "False"
EndSection

Section "Monitor"
    Identifier      "Monitor0"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Modeline        "1280x1024_75" 135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
    Option          "PreferredMode" "1280x1024_75"
EndSection

Section "Device"
    Identifier      "Device0"
    Driver          "nouveau"
EndSection

Section "Screen"
    DefaultDepth    24
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    SubSection     "Display"
        Depth       24
        Modes       "1280x1024"
    EndSubSection
EndSection

```

To find the right values for the modeline, I simply booted with the Nvidia driver, ran xvidtune (in the package x11-xserver-utils, the modeline given by gtf didn't work correctly for me): ```
xvidtune -show
```and copied the output to the xorg.conf.

---

### Post by MacUntu on 2010-09-16
Ok, if above doesn't work, maybe you are affected by this bug?

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

---

### Post by oasick on 2010-09-16
> **cariboo907 said:**
> I would help a lot if you told what make/model of video card you are using.

I have this card:

01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900XT] (rev a1)
But the nvidia drivers, don't works yet for this card (need the driver nvidia-173)  in xorg 1.9

---

