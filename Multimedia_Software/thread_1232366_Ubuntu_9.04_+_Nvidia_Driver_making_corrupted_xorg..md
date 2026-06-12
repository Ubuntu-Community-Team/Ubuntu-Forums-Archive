---
title: "Ubuntu 9.04 + Nvidia Driver making corrupted xorg.conf"
date: 2009-08-05
forum: Multimedia Software
---

### Post by shuffman37 on 2009-08-05
*Lately I've been having a mess of problems with Xorg failing to start and not leaving a log file for me to look at. I ended up looking at the Xorg.Conf the Nvidia driver makes and found out its a piece of crap. The references they use don't work and about 75% of the time it causes a blank screen on boot up. *

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-G220R"
    HorizSync       30.0 - 85.0
    VertRefresh     48.0 - 170.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1400x1050_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

_*Thats the one it made that doesn't work.*_

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Sony"
    ModelName      "Sony CPD-G220R"
    HorizSync       30.0 - 85.0
    VertRefresh     48.0 - 170.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Option         "NoLogo" "True"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1400x1050_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

*And the edited one that does. I'm sure for a novice this would be a major headache and nvidia-xconfig needs to be fixed so it works right.*

---

