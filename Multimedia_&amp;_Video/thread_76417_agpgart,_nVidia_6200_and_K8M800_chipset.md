---
title: "agpgart, nVidia 6200 and K8M800 chipset"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by david_finlayson on 2005-10-15
I've got a K8 Triton series motherboard with the VIA K8M800 chipset (AMD64 2800) and a nVidia 6200 video card.  I would like to enable AGP in the nvidia driver, but X becomes unstable when I try. Currently I have AGP turned off in my xorg.conf file:

```
Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA 6200"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAgp"                 "0"
        Option          "NoLogo"                "true"
        Option          "RenderAccel"           "true"
        Option          "HWCursor"              "true"
        Option          "CursorShadow"          "true"
        Option          "CursorShadowAlpha"     "64"
        Option          "CursorShadowXOffset"   "4"
        Option          "CursorShadowYOffset"   "2"
EndSection
```

If I turn it on, I start to get troubles:

```

        Option          "NvAgp"                 "2"

```

My system becomes unstable, freezes completely at random times (usually after some GL program has run such as a screen saver, but not always).

Is there something wrong? Should I expect AGP to work for this combination of chips?

Here is my modules file if that helps:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

via82cxxx
lp
mousedev
psmouse
agpgart
nvidia
```

Any ideas why AGP isn't working?

Thanks

David

---

### Post by david_finlayson on 2006-05-25
still not working...anyone have a clue?

---

