---
title: "[SOLVED] nvidia 7100, unknown chipset"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by mynameisflorian on 2008-01-12
Motherboard/Video Card Combo:
Biostar GF7100P-M7S (integrated Geforce 7100 chipset)

I've installed the restricted drivers, and ran nvidia-xconfig after the drivers alone didn't work. I looked in my /var/log/Xorg.0.log and found:
```

(--) PCI:*(0:16:0) nVidia Corporation unknown chipset (0x07e1) rev 162, Mem @ 0xed000000/24, 0xd0000000/28, 0xee000000/24

```
So, I looked up the chipset and found it is "almost" supported:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html)

The 7100 GS is supported, but it doesn't list the 7100 (w/o the GS). So I tried to force the chipset in my xorg.conf's device section:
```

Section "Device"
    Identifier     "NVidia GeForce 7100"
    Driver         "nvidia"
    #Chipset        "GeForce 7100 GS"
    #Chipset       "0x016A"
    ChipId         0x016A
EndSection

```

But, none of them did anything.

Any Ideas?

Thank you!!!
- Florian

---

### Post by mynameisflorian on 2008-01-12
yay! Got it to work. Envy to the rescue:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

