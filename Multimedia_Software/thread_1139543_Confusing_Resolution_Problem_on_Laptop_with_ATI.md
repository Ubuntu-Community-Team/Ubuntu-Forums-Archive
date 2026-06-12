---
title: "Confusing Resolution Problem on Laptop with ATI"
date: 2009-04-27
forum: Multimedia Software
---

### Post by JMacGill on 2009-04-27
I have a lapotp (Sony Vaio VGN-FW290 Series) with a 1920x1080 resolution screen and a monitor (Samsung 2232bw+) with a 1680x1050 resolution.

I have the latest ATI drivers from their website installed with 3D working.

It took many tries to get the monitor working with the Laptop LCD in mirror mode but I finally got that working, but now when I have the monitor disconnected, I can't get the resolution to go above 1680x1050.

Also, when I reboot, the resolution starts at 1680x1050 with the desktop at 1400x1050. Let me explain. In the settings, it says the desktop is at 1400x1050. The desktop starts at the left for the first 1400 pixels and then the 280 remaining pixels are junk.

here is my xorg.conf:
```
Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth    24
    SubSection "Display"
        Virtual    1680 2100
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Virtual    1680 2100
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    BusID       "PCI:1:0:0"
    Driver    "fglrx"
EndSection

```How do I get the system to boot at 1920x1080 when the monitor is not connected, and have the system support the monitor when it is connected without having this problem happen again?

---

