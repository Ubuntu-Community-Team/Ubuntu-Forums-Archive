---
title: "Triple monitor setup no longer working after installing Intrepid Ibex"
date: 2009-01-19
forum: Multimedia Software
---

### Post by rzax2 on 2009-01-19
Hi Everyone!

I "had" a working triple monitor setup (2 monitors on my pci-e card, 1 xserver, and an lcd tv running a seperate x server on a standard pci), but ever since updating from 8.04 to 8.10, I no longer have access to my tv.  Running nvidia-settings only shows GPO-0, the pci-e card, showing up.  My xorg.conf has both video cards in it.  I tried rolling my xorg.conf back to a file i saved off before updating my OS, but that doesnt solve the problem.

Any help on this would be appreciated.

Here is my setup:
2 x Gateway FPD1975W on GeForce 8800GT
1 x Samsung 32" LCD TV on GeForce 5200FX

Like i said before, this all worked absolutely flawlessly prior to updating to Ibex. Ive searched around this forums and tried to do a few manual xorg.conf edits, but nothing seems to work.

Here is my nvidia-settings generated xorg.conf file, so if there is any garbage in there, its probably its fault =p

#######################################################################
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1920 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "1"
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
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Gateway FPD1975W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       30.0 - 81.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:5:1:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: 1440x900_75 +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: 1440x900 +0+0"
# Removed Option "metamodes" "DFP-0: 1440x900_75 +1440+0, DFP-1: 1440x900_75 +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: 1440x900 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: 1440x900_75 +1440+0, DFP-1: 1440x900_75 +0+0; DFP-0: nvidia-auto-select +0+0, DFP-1: NULL; DFP-0: 1440x900 +0+0, DFP-1: NULL"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1200_60 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

#######################################################################

---

