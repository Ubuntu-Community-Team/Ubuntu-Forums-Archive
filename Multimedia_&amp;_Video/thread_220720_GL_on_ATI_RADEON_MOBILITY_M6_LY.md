---
title: "GL on ATI RADEON MOBILITY M6 LY"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by Efrain Valles on 2006-07-22
Did anyone get this to work?

I have been trying to get 3D accel to work with this card... ??? I read some posts but they all end without a final answer...

Thanks...

Viva la UBUNTU... :-D

---

### Post by gustl87 on 2006-08-16
hello

yes with the "radeon" driver - but it might freeze sometimes so you have to edit it in you xorg.conf as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

i found this at
[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

#sorry for my bad english.

---

