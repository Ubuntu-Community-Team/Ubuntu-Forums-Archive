---
title: "Primary Display (nvidia driver)"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by Kiri on 2008-04-13
I'm trying to set my primary display of a twinview setup to be the one on the right hand side. 
At the moment all the desktop icons, panel etc default to whichever display is on the left. 
I have checked the "make this display primary" in nvidia-settings, but it still does not help.


Here are the relevant sections of xorg.conf:

```
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L246WH"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0, DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1920+400; CRT: null, DFP: nvidia-auto-select +0+0"
EndSection
```

---

### Post by RTrev on 2008-04-13
I'd suggest you look at the nvidia-settings program.  That's how I always fine-tune my Twinview setups, and you should either already have it or you can easily grab it from the repositories.

HTH,
Bob

---

### Post by Kiri on 2008-04-15
I have been using the nvidia-settings program, but I still cannot get it to correctly display with the primary display on the right...

Has anyone got this working?
I really want to get it going...

---

### Post by Kiri on 2008-04-18
I think the problem is that linux views the extended desktop as one big display rather than seperate monitors. 
It should be relatively easy to get the desktop environment to put the icons on a certain display, or failing that to define the primary display starting from certain coordinates... but I cannot find a way :(
I guess no one else has tried this?

---

