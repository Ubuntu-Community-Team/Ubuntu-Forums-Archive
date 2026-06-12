---
title: "Forcing resolution (when monitor not turned on)"
date: 2010-10-20
forum: Multimedia Software
---

### Post by rafe101 on 2010-10-20
My mythbox is running 10.04. Normally, everything works just fine. When I turn the box on the TV turns on automatically and it starts up with the correct resolution. Occasionally, the TV doesn't come on automatically and needs to be turned on manually. If someone doesn't catch this fact soon enough, the resolution is an ugly, lower one, and the computer requires a reboot.

I would like it to boot up in the correct resolution whether the TV is on or not. I tried editing the xorg.conf, adding every bit of language I could find that might do this. I haven't broken the xorg.conf yet, but if the computer starts up without the TV on, it's still ugly. I'll attach the relevant section of the xorg.conf.

Any ideas?

Thanks in advance

```
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option "PreferredMode" "1360x768"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "EXAPixmaps"             # [<bool>]
    Identifier  "Card0"
    Driver      "nouveau"
    VendorName  "nVidia Corporation"
    BoardName   "NV34 [GeForce FX 5200]"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes     "1360x768"
    EndSubSection
EndSection
```

---

