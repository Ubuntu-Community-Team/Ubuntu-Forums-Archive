---
title: "Karmic: Can't set 1920x1200 on Geforce 210"
date: 2009-12-15
forum: Multimedia Software
---

### Post by fakada on 2009-12-15
Hi,

In windows my graphic adapter does 1920x1080. My card is an Asus EN 210 that coms with a Geforce 210 Chip.

On karmic the xorg.conf does not exist and the nvidia-settings does not allow resolutions higher than 1360*768. 

My LCD monitor is an LG Flatron W2243S.

Anyone helps?

lspci -v 
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce 210] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 8307
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at df00 [size=128]
    [virtual] Expansion ROM at c0000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

glxinfo | grep "renderer string"

OpenGL renderer string: GeForce 210/PCI/SSE2


Regards
Fak

---

### Post by dadrc on 2009-12-15
You might wanna check
```
xrandr
```to see if your hardware really supports that resolution.

If it does (that is, the resolution shows up in the output) you can just manually create an /etc/X11/xorg.conf or let the nvidia tool create one for you. The option is called 'Save to X Configuration file'.

---

