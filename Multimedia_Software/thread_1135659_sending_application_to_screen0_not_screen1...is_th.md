---
title: "sending application to screen0 not screen1...is that right?"
date: 2009-04-24
forum: Multimedia Software
---

### Post by eviltang on 2009-04-24
I have a dual video card/dual monitor configuration.

Running 9.04 (upgraded from 8.10) everything thing *seems* to be working ok (compiz, direct rendering, nvidia 1.80 drivers), but my question is this;

if I launch an application on screen1 via the gnome panel, it launches on screen0.  Is that right?  If I launch it via alt+f2 (on screen1) it opens on screen1.  That would be my preference for that panel.

I assume I need to create a new "top" panel for that screen1...is that right?  if so, what keywords/files/applications/packages should i be researching?  if there is no "out-of-the-box" solution, is it even possible to do via recompiling gnome and/or X?

Thank you very much for your time and input!

here is my xorg.conf for clarification:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
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
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"

    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2600"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 60.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
    Option         "Rotate" "CW"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by eviltang on 2009-04-24
update:  I have done a fresh install of 9.04 and still have the same issue.  any ideas?

thank you in advance.

---

