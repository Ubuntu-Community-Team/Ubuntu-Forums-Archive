---
title: "Configuring Totem Movie Player for TV-Out"
date: 2009-06-13
forum: Multimedia Software
---

### Post by BlueLion on 2009-06-13
Hi there,
can anybody help me to configure Totem Movie Player so that it plays on TV-Out?
The options "TV-Out in fullscreen by NVIDIA (NTSC)" and "TV-Out in fullscreen by NVIDIA (PAL)" are both greyed and thus not selectable.
Here's my xorg.conf:

 nvidia-settings:  version 1.0  (buildd@crested)  Mon Nov  3 08:46:04 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1" #TV
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 50.0
    VertRefresh     50.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0" #CRT
    VendorName     "Unknown"
    ModelName      "LG M1921A"
    HorizSync       30.0 - 70.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
    Option       "Connected Monitor" "Monitor1"
    Option       "TVStandard" "PAL-B"
    Option         "NoLogo" "true"
    Option         "TVOutFormat" "SVIDEO"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    16
    SubSection     "Display"
        Depth       16
        Modes       "800x600_50"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes       "1280x1024" "1024x768"
    EndSubSection
EndSection


Can anybody help me, please?

---

### Post by BlueLion on 2009-06-15
Nobody here familiar with Totem/Nvidia/TV-Out???

---

