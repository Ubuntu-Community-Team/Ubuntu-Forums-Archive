---
title: "NVidia triple monitor - xorg.conf problem?"
date: 2012-09-05
forum: Multimedia Software
---

### Post by McGyver81 on 2012-09-05
Hi everyone!

I have got a new video configuration, and I would like to set it up properly:
1 - Monitor 1600 x 900 (DVI connector)
2 - Monitor 1600 x 900 (DVI connector
3 - Projector  1920 x 1080 (HDMI connector)

The video card is an NVidia GTX 550 Ti 2GB.

I would like to set it up using the two monitors as one X screen using TwinView and the projector as a separate X screen on the right of the two monitors.

The xorg.conf script I came up with using the NVidia X server settings is:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver           "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver           "kbd"
EndSection

Section "Monitor"
    Identifier             "Monitor0"
    VendorName     "Unknown"
    ModelName       "Acer V203H"
    HorizSync            47.0 - 70.0
    VertRefresh      56.0 - 75.0
    Option                 "DPMS"
    # HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Monitor"
    Identifier             "Monitor1"
    VendorName     "Unknown"
    ModelName       "Seiko/Epson EPSON PJ"
    HorizSync            15.0 - 92.0
    VertRefresh      24.0 - 85.0
EndSection

Section "Device"
    Identifier          "Device0"
    Driver                "nvidia"
    VendorName  "NVIDIA Corporation"
    BoardName     "GeForce GTX 550 Ti"
    Option               "NoLogo" "True"
#    Option "RenderAccel" "1"
    BusID                  "PCI:3:0:0"
    Screen               0
EndSection

Section "Device"
#    Option "RenderAccel" "1"
    Identifier          "Device1"
    Driver                "nvidia"
    VendorName  "NVIDIA Corporation"
    BoardName     "GeForce GTX 550 Ti"
    BusID                  "PCI:3:0:0"
    Screen               1
EndSection

Section "Screen"
    Identifier             "Screen0"
    Device                  "Device0"
    Monitor                "Monitor0"
    DefaultDepth    24
    Option                 "TwinView" "1"
    Option                 "TwinViewXineramaInfoOrder" "CRT-0"
    Option                 "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1600+0"
    SubSection       "Display"
        Depth             24
    EndSubSection
EndSection

Section "Screen"
    Identifier              "Screen1"
    Device                   "Device1"
    Monitor                 "Monitor1"
    DefaultDepth    24
    Option                  "TwinView" "0"
    Option                  "metamodes" "DFP: 1920x1080 +0+0"
    SubSection         "Display"
        Depth               24
    EndSubSection
EndSection

```

Of course there is something wrong in here... because I'm not getting anything on the projector.

Does anyone have any clue on how to solve this problem?

Thank you in advance

---

