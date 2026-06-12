---
title: "Karmic - Quad Monitor Woes, Compiz"
date: 2009-11-26
forum: Multimedia Software
---

### Post by Lash15b on 2009-11-26
Hi Chaps, (My first ever forum post!)

I have been using Ubuntu for about a year now and have recently upgraded to Karmic (Which I am loving by the way) I have been given a bunch of monitors and dug out some graphics cards but for the life of me I cannot figure out how to get them operating together. - My goal is to get them operating in some form of Compiz 'shared desktop environment' with all of the associated bells and whistles. 

Hardware: Nvidia FX5500 AGP, Nvidia FX5200 PCI, 2 x 19" 2 x 15"

I have screwed up my xorg.conf many times trying to get the four monitors playing nice, my current working xorg (which has two monitors running off the FX5500) is shown below - I can see that the monitors are detected when I run gksudo nvidia-settings and it shows me GU0 and GU1 (The actual cards) and the monitors are detected. When I try and enable them through the Nvidia settings and save them off, they just dont work.

I am running Nvidia drivers 173 (180 really screws with my machine and refuses to work). Whether I use xinearma or compiz I just cannot get my other two monitors to work.

Some advice from a veteran on how I can alter my xorg to show the second Nvidia card, along with two additional monitors would be most appreciated!

Thanks Very Much....

Xorg:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD Hanns.G HC174"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
    BusID          "PCI:1:0:0"
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
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

