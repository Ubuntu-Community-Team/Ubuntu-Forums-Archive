---
title: "Blank strip on right (HTDV mode)"
date: 2008-10-18
forum: Multimedia Software
---

### Post by odror on 2008-10-18
I have kubuntu 8.10

Nvidia 7600gt

I tried using drivers 177.80, and a few other recent drivers. The problem in all the drivers.

I have dual monitor. the second monitor is an old HTDV with component input from my nvidia card. The second monitor has a blank strip on the right side.

The same monitor was working fine with fedora core 6 (different version of the nvidia driver), but with the same xorg.conf file.

(that older version of the nvidia driver cannot ne compiled on the new kernel)

In a console more when i type the X commnad I do not get the
blank strip, but when i type startx or use the kde manager I get it.


Section "Monitor"

    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    ModeLine       "1080i" 74.52 1920 1952 2016 2208 1080 1084 1096 1126 -hsync -vsync interlace
    Option         "DPMS"
EndSection

Section "Screen"


#    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: 1920x1080"
    Option         "TVOutFormat" "COMPONENT"
    Option         "TVStandard" "HD1080i"
    Option         "ConnectedMonitor" "CRT-0,TV-0"
    SubSection     "Display"
        Depth       24
        Modes      "1080i"
    EndSubSection

EndSection

Thanks
Oz

---

