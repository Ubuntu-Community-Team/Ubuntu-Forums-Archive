---
title: "Possible to have 4 panels with one X server using nVidia?"
date: 2011-04-30
forum: Multimedia Software
---

### Post by dboy on 2011-04-30
I'm SOOOO excited! ALMOST have this thing working. So close I can taste it. I am a trader suffering under the blight that is Windows, never able (until now) to get my 4-panel setup working. I have 4 identical Samsung 213T panels, and 2 nVidia dual-DVI cards. Am running the nVidia driver listed as (version current) on Ubuntu 11.04 Natty. No idea where the driver is installed so can't give the real version number. I think it's the one that is NOT version 173. It is listed as the "recommended" driver for Ubuntu 11.04 Natty.

Have good display on all 4 panels now (I will post the config below). I can move the mouse across panels with no issues. The problem is that I cannot drag applications left to right, only up and down. I have left-above/left-below set up as Twinview, and right-above/right-below also set as Twinview.

I can drag windows between 2 monitors (above and below) no problem, but not left and right. I assume this is because I have 2 X severs going (that's just the theory I am working from). No idea how to correct that in the config. What am I doing wrong? Huge appreciation to everyone in advance. Will post the resulting working config if I get one.


```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:5:0:0"
EndSection

Section "Screen"

# Removed Option "TwinViewXineramaInfoOrder" "DFP-0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+1200, DFP-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +0+1200"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +0+1200"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+1200, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

