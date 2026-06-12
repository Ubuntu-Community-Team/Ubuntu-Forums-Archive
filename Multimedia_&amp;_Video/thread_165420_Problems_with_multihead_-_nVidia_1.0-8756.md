---
title: "Problems with multihead - nVidia 1.0-8756"
date: 2006-04-24
forum: Multimedia &amp; Video
---

### Post by ckrueger on 2006-04-24
In earlier driver versions (1.0-8174 and prior), I was able to configure each output on a dual-head card as its own individual device.  This was useful because the two displays on this card are totally different (one DVI, 1280x1024, the other standard D-sub, 1024x768 ).  Also, this is a tri-head setup, so not having to mess with TwinView made the setup unbelievably easy.  Below are the device sections in my xorg.conf as they were before the driver update (which was included in the update to 6.04):

```
Section "Device"
        Identifier      "NVIDIA GeForceFX 5600 Center"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "ConnectedMonitor"      "dfp"
       Screen          0
        Option          "RenderAccel"   "true"
EndSection

Section "Device"
        Identifier      "NVIDIA GeForceFX 5600 Left"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "ConnectedMonitor"      "crt"
       Screen          1
        Option          "RenderAccel"   "true"
EndSection
```

Since the update, I have rewritten both device statements from scratch screwing with the presence (and settings) of the "Screen" and "ConnectedMonitor" arguments, but nothing has yielded the correct effect.  Whenever starting X now, it says that the device PCI:1:0:0 is already in use, and removing that statement keeps the device from even being acknowledged.

Has anyone successfully configured their nVidia setup with the new 8756 driver *WITHOUT* using TwinView?  I'd appreciate any help I can get.  Thanks!

Regards,
Campbell Krueger

---

### Post by ckrueger on 2006-04-24
It looks like I answered my own questions after another ~10 minutes of dickin around with it.  Hopefully my X config will help answer other peoples' questions in the future:

```
Section "Device"
        Identifier      "Center"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "UseDisplayDevice"      "DFP-0"
        Screen  0
EndSection

Section "Device"
        Identifier      "Left"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "UseDisplayDevice"      "CRT-0"
        Screen  1
EndSection

Section "Device"
        Identifier      "Right"
        Driver          "nvidia"
        BusID           "PCI:2:1:0"
        Option          "RenderAccel"   "true"
EndSection

Section "Monitor"
        Identifier      "Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Center Screen"
        Device          "Center"
        Monitor         "Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Left Screen"
        Device          "Left"
        Monitor         "Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Right Screen"
        Device          "Right"
        Monitor         "Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Center Screen"
        Screen          "Left Screen" LeftOf "Center Screen"
        Screen          "Right Screen" RightOf "Center Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "on"
EndSection
```

Regards,
Campbell Krueger

---

