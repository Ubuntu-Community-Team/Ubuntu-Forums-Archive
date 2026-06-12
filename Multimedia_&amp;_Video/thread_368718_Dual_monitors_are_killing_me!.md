---
title: "Dual monitors are killing me!"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by Elpram on 2007-02-23
Okay, so I can get TwinView working, however it only ever seems to use my CRT, not my LCD as default display.  This is not what I want, but any attempt to change it either crashes my X system, or results in only one of the two monitors working.  below is my xorg.conf file, set up so that only my LCD is working:

```

Section "Monitor"
    Identifier     "DFP"
      VendorName   "Metro"
    Option         "DPMS"
EndSection

Section "Monitor"
       Identifier   "CRT"
      VendorName   "ViewSonic"
       Option      "dpms"
EndSection


Section "Device"

#	Option		"UseFBDev"		"true"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID		"PCI:1:0:0"
    Option "TwinView" "True"
#    Option "TwinViewOrientation" "RightOf"   
#    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1680x1050_60, 1280x1024;1280x1024,1280x1024"
    Option "UseDisplayDevice" "DFP-1"
#    Option "ConnectedMonitor" "DFP-1,CRT-0"
#maybe DFP instead
EndSection


Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "CRT"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050_60" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by majoridiot on 2007-02-24
instead of trying to do it all by hand, run:

```
sudo nvidia-settings
```

make your adjustments, save and restart X if need be (ctrl-alt-bkspc).

---

### Post by kerry_s on 2007-02-24
the command is> sudo nvidia-xconfig --twinview

---

