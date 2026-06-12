---
title: "TwinView problem: trying to get connected Samsung 19'' monitor to the laptop"
date: 2009-07-11
forum: Multimedia Software
---

### Post by Malfet on 2009-07-11
Hi all,

I'm trying to connect Samsung SyncMaster 913V monitor to my laptop with NVidia graphic card. I play around with xorg.conf manually and with nvidia-settings GUI and now I have a picture both at the laptop screen and the second monitor, but the monitor shows only small part of the screen in resolution 640x480. What shall I change in my xorg.conf to get 1024x768 resolution? 
Here is my xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
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
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1024x768"
    HorizSync       31.0 - 48.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200 32M/64M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1024 768
        Depth       24
        Modes      "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: 1024x768 +0+0; CRT: nvidia-auto-select +0+0, DFP: NULL"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I will be very grateful for any help!

---

### Post by HappyFeet on 2009-07-11
Are you opening nvidia-settings with:
```
gksudo nvidia-settings
```?
Then go to X Server Display Configuration and click on the display you want to change. Change Resolution, click apply, and Save to X configuration file. Reboot.

---

### Post by Malfet on 2009-07-11
> **HappyFeet said:**
> Are you opening nvidia-settings with:
```
gksudo nvidia-settings
```?
Then go to X Server Display Configuration and click on the display you want to change. Change Resolution, click apply, and Save to X configuration file. Reboot.

Thanks for you answer, but there is no 1024x768 resolution there. If I go there I can choose only between 640x480 and 320x240 for the external monitor :(

M.

---

### Post by HappyFeet on 2009-07-11
Do you have the proper video driver installed?

---

### Post by Malfet on 2009-07-11
> **HappyFeet said:**
> Do you have the proper video driver installed?

Ya, I think so. I have NVidia 173 driver running right now.

---

