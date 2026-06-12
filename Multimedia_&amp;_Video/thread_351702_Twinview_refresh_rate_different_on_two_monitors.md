---
title: "Twinview refresh rate different on two monitors"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by gumbald on 2007-02-02
I've got identical displays from my 6600GT, however the only refresh rate option I have from my menu is 75Hz, when I would like them to both run at 60Hz.

After checking, it now appears that one monitor is running at 75Hz, but the other is managing 60Hz.

Here's my relevant xorg.conf sections, hope someone can help me fix them both to 60 :)

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "IgnoreEDID" "yes"
    Option "SecondMonitorHorizSync" "28.0 - 64.0"
    Option "FirstMonitorVertRefresh" "60.0"
    Option "SecondMonitorVertRefresh" "60.0"
    Option "Xinerama" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "CRT"
EndSection
```

---

### Post by gumbald on 2007-02-02
Fixed it, replaced:

```
    Option "FirstMonitorVertRefresh" "60.0"
    Option "SecondMonitorVertRefresh" "60.0"
```

with:

```
    Option "HorizSync"   "CRT-0: 28.0 - 64.0;  CRT-1: 28.0 - 64.0"
    Option "VertRefresh" "CRT-0: 60;  CRT-1: 60"
```

:D

---

### Post by MystikIncarnate on 2007-12-24
thank you! i will try this!!!

i've been so stumped on this since i GOT twinview running... hopefully this works!

---

### Post by MystikIncarnate on 2007-12-24
Someone should really document this somewhere (maybe in the Wiki) for Twinview Sync and Refresh rate changings... so many seem to have a problem with the nVidia drivers and the Sync rates for monitors... this could really help.

P.S. THANK YOU SO MUCH!!

When my Samsung Syncmaster 1100p is at 1600x1200, and any refresh higher than 60Hz, there's a visible "wobble" to the image, where it will shake, only a few pixels, back and fourth... gives me a freakin migrane!  but at 60hz for WHATEVER reason, it doesn't do this.  This was the ONLY information that STOPPED THE SHAKING! you saved my BRAIN!

---

