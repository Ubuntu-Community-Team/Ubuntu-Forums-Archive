---
title: "need a bit of help with twinview"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by bapho on 2007-01-09
heya im kinda new to this so any help would be great
i have a 6600GT with dvi and vga outputs and 2 benq lcd monitors (a 15'connected via vga and a 17' connected via dvi) when i installed the nvidia drivers only the 15' would work after i editted the xorg.conf according to the guide thats stickyed in the forum only the 17' will work im a bit confused
any ideas?
XORG.conf

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0" 
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768;800x600,800x600"
    Option "ConnectedMonitor" "DFP, CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by ict on 2007-01-09
Delete the "ConnectedMonitors" - Line. Helped me.
According to the nVidia Documentation, this option should only be used if there are problems with the auto-detection.

---

