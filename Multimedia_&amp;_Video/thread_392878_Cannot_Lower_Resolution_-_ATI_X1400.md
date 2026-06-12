---
title: "Cannot Lower Resolution - ATI X1400"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by varig77 on 2007-03-25
I was wondering if someone could tell me how to lower the screen resolution. I have read numerous threads here and there; however,  I cannot find a solution that would work for me. I have a Dell 6400 laptop running Ubuntu 6.10 with an ATI X1400 graphics adapter and a screen that supports resolutions up to 1680x1050. I've installed the latest fglrx driver and my current resolution is set to 1680x1050. I am not able to lower the resolution to 1280x800. 

Here is an output of fglrxinfo:

```
owner@mango:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

... and my /etc/X11/xorg.conf

```


Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
         # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
        Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes     "1280x800"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection


```

Any help is much appreciated.

---

