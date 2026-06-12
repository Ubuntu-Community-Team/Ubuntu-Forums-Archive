---
title: "Strange video glitch"
date: 2009-07-07
forum: Multimedia Software
---

### Post by Sankou on 2009-07-07
I'm fairly new to Ubuntu and I've been running into an issue with my video/video driver (I assume). When I run certain programs or commands my system locks up a bit and starts to run slowly. Black bars blink and jump up and down the screen and everything runs very glitchy, frame by frame kind of. This didn't occur until after I install my video driver.  I think I just configured something wrong... or not at all. Here some info about my computer.

Ubuntu 9.04, up to date

  *-display               
       description: VGA compatible controller
       product: RV730XT [Radeon HD 4670]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

The actual hardware specifications of my video card are:

ATI Radeon HD 4670
Brand: HIS
Interface: PCI Express 2.0 x16
Core Clock: 780MHz
320 Stream Processors
Memory Clock: 2000MHz
512 MB GDDR3
128-bit
DirectX 10.1
OpenGL 2.0

Any information about why this happens would be very much appreciated! :)

~Thanks for looking.

---

### Post by Sankou on 2009-07-07
Here's some more info:

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection

---

### Post by Sankou on 2009-07-07
:confused:

---

