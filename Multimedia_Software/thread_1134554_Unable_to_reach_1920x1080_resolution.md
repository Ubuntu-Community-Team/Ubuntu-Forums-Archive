---
title: "Unable to reach 1920x1080 resolution"
date: 2009-04-23
forum: Multimedia Software
---

### Post by Morsvir on 2009-04-23
I'm using Ubuntu 9.04 with an ATI Radeon HD 4870 and cannot get my display above 1776x1000. I'm new to Linux so I don't know for sure what information I should provide you all by default, but the xorg.conf seems to be popular with graphics problems:


> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "vesa"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    SubSection "Display"
        Virtual   3056 1024
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3056 1024
        Depth     24
    EndSubSection
EndSection


Thanks ahead of time for any help you can give.

---

