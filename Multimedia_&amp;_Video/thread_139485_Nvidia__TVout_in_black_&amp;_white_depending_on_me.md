---
title: "Nvidia : TVout in black &amp; white depending on metamodes !"
date: 2006-03-04
forum: Multimedia &amp; Video
---

### Post by DidRocks on 2006-03-04
Hello!

First of all, i apologize for my bad english, i'll try to make it as good as i can:

I've had a geforce ti 4, which had worked very well. Recently, i decided to by a geforce A6600 GT.

I thougth, i could keep my xorg.conf, but, well, with some modification, i obtain this :

```
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "NoLogo"
        Option "RenderAccel" "Enable"
# Double Ecran
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "PAL-N"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"
Option "MetaModes" "1280x1024;1024x768,1024x768"
EndSection
```

(i use "PAL-N" cause i'm a french guy)

I can switch on my tv in doing xrandr -s 1. The mater is that the tv is in black and white...

I tried :
Code:

```
Option "MetaModes" "1024x768,1024x768;1280x1024"
```

Under gdm, i'm in 1024x768 resolution, and then, when gnome is starting, i'll get back my 1280x1024 (chosen as default in gnome preferences). With xrandr -s 0, i can switch on my tv and i get colors !!!

So, what's the matter? I get a big issue, with that configuration (i don't have this matter with the first Metamodes agency) : each time i leave gnome, he freeze (even if i just want to change my session and the screen is scrambled!
Is there a solution?
thaks in advance!

---

