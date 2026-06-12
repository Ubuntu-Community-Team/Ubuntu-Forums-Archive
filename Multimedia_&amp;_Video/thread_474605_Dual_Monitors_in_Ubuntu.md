---
title: "Dual Monitors in Ubuntu"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by JoeeT on 2007-06-15
Simple question. Is it possible to set up Dual Monitors in Ubuntu?

Is there a simple tutorial for how to do it?

N.B - One monitor will be directly connected to a VGA port, and the other will be connected to a DVI-VGA adapter in the DVI port. Both ports are on the same card.

Cheers

---

### Post by OoooMatron on 2007-06-15
if you have nvidia , it's really easy

Section "Device"
        Identifier      "nVidia Corporation NV35 [GeForce PCX 5900]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Option          "TwinView"      "true"
EndSection


this setups dual monitors with the visual effects.  enabling twinview should be enough (you only need one monitor definition in /etc/X11/xorg.conf, not two.

---

