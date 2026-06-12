---
title: "Radeon HD 4850 drivers"
date: 2009-10-10
forum: Multimedia Software
---

### Post by blueflinko on 2009-10-10
I have duel monitors running on a Radeon HD 4850 video card. I tried to install the "radeonhd" driver then edited the xorg.conf file to look like this... 

Section "Device"
    Identifier    "Default Device"
    Driver        "radeonhd"            
        Option        "DRI" 
    Option        "AccelMethod" "EXA"
    Option        "Monitor-**DVI-D_1**" "Monitor1"
    Option        "Monitor-**DVI-D_0**" "Monitor2"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
EndSection

Section "Monitor"
    Identifier    "Monitor2"
    Option        "RightOf" "Monitor1"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection


This caused the whole system to work but in Mirror and then the Display Preference when opened causes the whole system to bog down.  I have to uninstall the driver to get any sort of functionality.

Anyone have an idea on how I can get my video card to work?

---

