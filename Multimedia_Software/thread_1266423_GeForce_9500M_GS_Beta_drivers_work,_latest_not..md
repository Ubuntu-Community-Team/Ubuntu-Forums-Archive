---
title: "GeForce 9500M GS: Beta drivers work, latest not."
date: 2009-09-14
forum: Multimedia Software
---

### Post by mediajunkie on 2009-09-14
Hi, 

I need some help / input with my driver problem. Let me explain...

_first my configuration:_ 

[INDENT]Ubutnu Hardy // Kernel: 2.6.24-24-generic
Acer Aspire 8920G
Video: GeForce 9500M GS Turbocache
Current driver NVIDIA-Linux-x86-180.17 (beta) 
Last tried driver:  NVIDIA-Linux-x86-185.18.36[/INDENT]

_Issue:_

[INDENT]I've been running this Beta driver with only few issues (compiz not working properly) 
However, I thought it is time to update to the latest stable driver.
In the past I've tried with other versions between latest and that beta, but every time without success. Also this time, the new driver won't be loaded, no matter what I do. 

Going back to the beta driver still works. Does anybody have a clue why only that one beta works? (also a previous version 177.80 won't work) Every time I try a newer driver, the nvidia drivers can't be loaded. [/INDENT]

_procedures of install: _


[INDENT]Go to terminal
kill X 
become root
run the script sh NVIDIA-Linux-x86-185.18.36-pkg1.run
and then either create new xorg.conf, or even copy the working from previous dirver
Restart X[/INDENT]

At this stage, non of the drivers I've tried load, only the one Beta (180.17) works. 
Would appreciate some input why this is happening. Thanks in advance. 




ADD-ON:  (Attachment: xorg.conf & xorg.log)

**_xorg.conf_**

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
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
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Philips 170S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500M GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500M GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024_75 +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

