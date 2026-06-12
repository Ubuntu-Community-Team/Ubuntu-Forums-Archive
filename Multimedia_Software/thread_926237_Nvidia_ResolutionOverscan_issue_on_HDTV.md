---
title: "Nvidia Resolution/Overscan issue on HDTV"
date: 2008-09-21
forum: Multimedia Software
---

### Post by unsungboxer on 2008-09-21
Hello,

I have been working on this for weeks.  I am trying to connect my ubuntu box to my hdtv for multimedia purposes.  However after following every guide out there, I am still stuck using a stretched resolution or overscan.  Right now I have the option of 1024x768 which is stretched, or setting it to 1280x720 which overscans and cuts off all edges of the screen (cannot see title bar etc).  All other resolutions cause flickering.

I have tried altering xorg (nvidia-settings doesnt seem to recognize changes), I have used nvidia-settings (1366x768 res doesn't exist).  Tried altering system/preferences/screen resoltion (1366x768 res does not exist).  I have tried using xvidtune, it doesn't apply any changes or seem to do anything for that matter.  Used envy built nvidia driver, no difference.

Help!  I am at my wits end!

Setup:
Philips HDTV (1366x768)
Nvidia 6800gs
DVI to HDMI Adapter
AMD Athalon 64
Ubuntu 8.08
envy built nvidia drivers.

xorg.conf readout:

> 
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Philips FTV"
    DisplaySize     345    195
    HorizSync       15.0 - 50.0
    VertRefresh     48.0 - 62.0
    ModeLine       "1360x768" 84.8 1365 1384 1516 1792 768 786 792 798 -hsync +vsync
    Option         "UseEdidDpi" "FALSE"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GS"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1360x768 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


---

### Post by udude on 2009-08-15
I bumped into this overscan issue a while ago and reverted to use 1366x768 on the VGA d-sub connector (which works well but not crisp as DVI).
My setup:

[INDENT]9.04
GeForce 7950 GT (dual DVI-out)
Samsung 40" LN-S4051D TV
[/INDENT]
Were you able to resolve this?

---

