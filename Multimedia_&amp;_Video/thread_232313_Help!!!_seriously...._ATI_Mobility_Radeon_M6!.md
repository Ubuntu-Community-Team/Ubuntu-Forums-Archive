---
title: "Help!!! seriously.... ATI Mobility Radeon M6!"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by MiniZiper on 2006-08-08
Ok, I have a laptop running WinXP and Kubuntu Dapper (well, dont know the name, but its the latest one...)
My problem is that.... it crashes... and its not once, its many times. First, I found out it was my transulency effect, so I disabled it, it became more stable. Now, it crashes when I use swiftfox (or konqueror).
I am using a Compaq Presario 1700 1.2GHz (<-- Upgraded it myself..) using an ATI Radeon Mobility M6 (<-- I've read it cuases problems sometimes, stability problems on Linux)
I am 100% sure its not overheating (I play 3D Games on WinXP)
I REALLY don't want to stop using Linux. I changed in X.CONF my drivers to "radeon" (like somebody suggested on another thread) but it still crashes.

Any help would be greatly appreciated[-o<

---

### Post by MiniZiper on 2006-08-08
lol, well i think its stable now that I'm using Opera... so something is wrong with konqueror and firefox...

---

### Post by gustl87 on 2006-08-16
hello

i am using an ati m6 - and i got the same strange freezes.

but then i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and it worked after some modifications.
so it never freezed again (till now).

so you should use the driver called "radeon" and if freezing continues, you might edit it as follows:

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

#sorry for my bad english.

---

