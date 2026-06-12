---
title: "lucid lynx sets large screen resolution after kernel update"
date: 2010-05-06
forum: Multimedia Software
---

### Post by zuker on 2010-05-06
after first kernel update after loading Xserver (even in safe graphics mode) my monitor says
"Not Optimum Mode
Recommended Mode: 1440x900 60Hz"
(just after install, before update everything has been ok)

Monitor: Samsung SyncMaster 923NW
Card: GeForce 7900

```

$cat /etc/X11/xorg.conf
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth  24
    SubSection "Display"
        Viewport 0 0
        Depth  24
        Modes "1440x900_60.00"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Indentifier    "Default Device"
    Driver  "nvidia"
    Option  "NoLogo"    "true"
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    ModeLine "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932 -HSync +VSync
EndSection

```

```

$DISPLAY=:0.0 xrandr
Screen 0: minimum 800 x 600, current 2048 x 1536, maximum 2048 x 1536
default connected 2048x1536+0+0 0mm x 0mm
2048x1536    60.0*
1280x1024    61.0
1024x768     61.0
800x600      61.0
$DISPLAY=:0.0 xrandr --newmode "1440x900_60"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
$DISPLAY=:0.0 xrandr --addmode default 1440x900_60.00
$DISPLAY=:0.0 xrandr --output default --mode 1440x900_60.00
xrandr crtc 0 failed
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 24 requests (22 known processed) with 0 events remaining.

```

thank you for tour help!

---

### Post by MS-Hater on 2010-05-06
were you compiling the kernel from source? if so, were you using the Ubuntu source or source from elsewhere (like [www.kernel.org)?](www.kernel.org)?) did you remember to recompile & install the NVIDIA kernel module? answer those, and I'll be able to help more.

---

### Post by zuker on 2010-05-07
i didn't compiled kernel sources. i mean regular ubuntu updates.

---

### Post by zuker on 2010-05-10
bump...
thanks for help

---

### Post by heatpumpcontrol on 2010-05-22
same here..

---

