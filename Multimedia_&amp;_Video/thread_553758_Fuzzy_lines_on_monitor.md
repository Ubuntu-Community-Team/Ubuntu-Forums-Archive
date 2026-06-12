---
title: "Fuzzy lines on monitor"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by acl123 on 2007-09-18
Hi, since I installed Ubuntu a month ago I've been trying to get rid of the fuzzy vertical lines on my monitor but with no success. This looks like a potential Ubuntu killer for me. I'll probably have to go back to Windows if I can't resolve it, which is a pity because I've managed to get most of the other components of my system working over the past month.

My monitor is a VG2021m. I have a GEForce 7300 GS which I installed using Envy.

I have found differing settings out there for HorizSync and VertRefresh but I have tried them all. I am running at the recommended resolution 1400x1050/60 and I have run gtf to get the rest of the mode line value.

The monitor and device sections of my xorg.conf looks like this -

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "VG2021m"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Modeline       "1400x1050_60.00"  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -HSync +Vsync
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver         "nvidia"
    Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
EndSection

```

I'll be very grateful for any insight.

---

