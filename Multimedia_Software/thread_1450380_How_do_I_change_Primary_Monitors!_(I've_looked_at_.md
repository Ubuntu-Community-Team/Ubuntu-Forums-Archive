---
title: "How do I change Primary Monitors! (I've looked at other forums already!)"
date: 2010-04-09
forum: Multimedia Software
---

### Post by abelis on 2010-04-09
I cannot figure out how to change my primary monitor!

My xorg.conf looks really different from the ones I've seen people post. Any help!?

xorg.conf ::

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        SubSection "Display"
                Virtual 3200 1080
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

:confused:

---

