---
title: "nvidia tv out issue"
date: 2008-09-04
forum: Mythbuntu
---

### Post by mark467 on 2008-09-04
i had my new front end setup working great, then moved it to the tv and the screen is diagonal lines and like its out of sync
if the lcd is plugged in i cant get tv out 
when i vnc in with the tv plugged in the screen is to small and i cant get in nvidia-settings. here is the sections of my /etc/X11/xorg.conf


Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
 Option         "NoLogo" "1"
    #Option         "UseDisplayDevice" "TV"
    Option         "ConnectedMonitor" "TV"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce3 Ti 200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select" "1920x1080" "1280x720$
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
EndSection

what needs to be changed for use with regular tv svideo??

---

