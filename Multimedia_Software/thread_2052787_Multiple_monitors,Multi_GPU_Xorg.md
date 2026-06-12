---
title: "Multiple monitors,Multi GPU Xorg"
date: 2012-09-04
forum: Multimedia Software
---

### Post by tesla.coil on 2012-09-04
Hi Folks,

I have a host with 2 Nvidia GPUs in it with 2 monitors connected to each card.For the first GPU,i have 'Twinview' enabled with 'Rightof' twinview orientation (using the monitors connected to first card).Now,id like to use the secondary card and clone the Screen 0 from primary GPU.

That is .. the display from secondary gpu should be a clone of primary gpu,with the twinview+rightof on .

Although,i have been able to get this to work,(cant see the mouse pointer on the monitors connected to secondary GPU) but the OpenGL doesnt work on the secondary GPU.Is it fixable? Or may be can i have OpenGL apps to work on 2 monitors ,one from the primary card and one from secondary,instead of all the 4 ??

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
    FontPath        "/usr/local/share/fonts/ttfonts"
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
    ModelName      "DELL U2311H"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL U2311H"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1700"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AllowGLX" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "PixmapCacheSize" "70000"
    Option         "DamageEvents" "True"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1920x1080 +1920+0, DFP: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AllowGLX" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "PixmapCacheSize" "70000"
    Option         "DamageEvents" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1920x1080 +0+0, DFP: 1920x1080 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

