---
title: "Dell Inspiron 1000 Xubuntu 800x600 Resolution"
date: 2009-09-29
forum: Multimedia Software
---

### Post by edoss on 2009-09-29
I am new to Ubuntu and Linux - when this notebook crashed under WinXp Home - I decided it was time to see if the grass was really greener. I have been able to get everything that I need to work including my wireless adapter. The one thing that I am having trouble with is getting my screen resolution to 1024 x 768 - right now I am stuck at 800 x 600. I will not be needing or using 3D or any gaming.

I read so many threads about this issue, but there were so many variations - where to start? I have the SiS 650 chip set (which is working fine at 800 x 600). I found the an updated Linux driver on the SIS website and down loaded it to my Desktop, but the Hardware Driver app does not find it. I have not tried to hand modify my xconf file, becuase at this point I am not sure what to change.

*-display UNCLAIMED
description: VGA compatible controller
product: 65x/M650/740 PCI/AGP VGA Display Adapter
vendor: Silicon Integrated Systems [SiS]
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-2.0 cap_list
configuration: latency=0

Any help would be appreciated.


= = = = =
*Mörgæs 2014-6-2: This is likely to be fixed in 14.04*

---

### Post by HappyFeet on 2009-09-29
Post the output of:
```
mousepad /etc/X11/xorg.conf

```

---

### Post by hellrazor35 on 2009-09-29
I too have the exact same problem.

xorg.conf code as follows

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

