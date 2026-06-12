---
title: "Unity only works with dual screen (not on laptop standalone)"
date: 2011-06-27
forum: Multimedia Software
---

### Post by SteveH1UK on 2011-06-27
Hi

I have a Lenovo G550 with a GeForce G210M Graphics processor.

I use twinview when I plug in my 23" Samsung monitor (1920x1080) into my laptop and this works fine with Unity. I have my laptop (1366x768) configured  as the primary display.

If I start up with just my laptop in Unity the resolution is all wrong (it seems to be using the 1920x1080 display). Now if I start up my laptop in "Ubuntu classic" it displays fine.

When I upgraded to 11.04 I was in twinview mode. Not sure if this is significant.

Here is the display part of my xorg.conf file
--------------------------------------------------

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LEN"
    HorizSync       38.2 - 47.4
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G210M"
EndSection


Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G210M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

   Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

   Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

