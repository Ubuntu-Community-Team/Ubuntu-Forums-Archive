---
title: "Shuttle sk83g and LG L1800PK"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by Peasant on 2006-08-28
Hi,

I've just installed Ubuntu 6.06 on a Shuttle SK83G (UniChrome Pro 3D Graphic Controller) with an LG L1800PK monitor. All appears to be well, except the highest screen resolution I can set is 1024 x 768, and this monitor can support 1280 x 1024. I'm not sure if it is the graphics or the monitor that has not been detected properly, so can someone point me in the right direction? TIA.

---

### Post by z4ziggy on 2006-10-17
i have the same monitor, and although according to specs it can do better than the settings im using (refresh rate 75) im using the followings :

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "Flatron L1800PK"
    HorizSync       31.5 - 80.5
    VertRefresh     20.0 - 60.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "Coolbits" "1"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

```
hth

---

