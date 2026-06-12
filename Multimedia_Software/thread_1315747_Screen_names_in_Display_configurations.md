---
title: "Screen names in Display configurations"
date: 2009-11-05
forum: Multimedia Software
---

### Post by stz_comp on 2009-11-05
Hi,

I've a little problem, nothing serious, but it's quite irritating. I have AMD64 Ubuntu Jaunty with 9.6 fglrx driver of my Ati Radeon HD 3450 graphic card and two monitors. This is the only version of driver, that is working properly on my PC, but In Display configurations are both screens called as Unknown. Is there a way how to call them in xorg.conf? My attempts of configuration usually last with black screen after boot. :D
Thanks.

This is my xorg.conf:

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Virtual    3200 1080
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection

---

