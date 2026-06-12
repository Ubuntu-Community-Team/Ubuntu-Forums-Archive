---
title: "Nvidia 180.22 driver and dual screen monitor problems"
date: 2009-02-07
forum: Multimedia Software
---

### Post by klemperal on 2009-02-07
This has been driving me half crazy all day :p.  I've been trying to get my tv working as a seperate x display via s-video out, but no luck so far--all I'm getting is a black screen.  I had things working with the 173 drivers, but of course the 173 driver had other problems I was hoping the 180.22 would fix.  I'm using Ubuntu intrepid and a Nvidia 8400gs.  Below is my xorg.config.  Some help would be really appreciated.

```
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E151FPb"
    HorizSync       31.0 - 60.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1024x768_75 +0+0; CRT: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768_70 +0+0; CRT: 1024x768_75 +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "TV: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1024x768 +0+0; TV: 800x600 +0+0; TV: 720x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by klemperal on 2009-02-07
bump

---

### Post by norwoods on 2009-02-07
have you tried the nvidia-settings program?

---

### Post by klemperal on 2009-02-07
I have.  Thats where I've been attempting to get a separate x screen working.  Unfortunately for me I've still got a blank second monitor.

---

