---
title: "Poor 2/3D performance with ATi Mobility HD4570"
date: 2009-11-15
forum: Multimedia Software
---

### Post by miech on 2009-11-15
I recently installed Karmic on my laptop in a dual boot with Vista (for some apps I need to run at work). So far, anything works the way it should, except the desktop. Seen the specifications of the video card it should run smoothly and fast, but it runs like anything is rendered over the CPU. Any thoughts?

Here is the output of lspci | grep ati:
```
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```
There are two video cards shown, as there are two in my laptop. The HD3200 is for saving energy, but I rather use the better performing HD4570. Saving energy isn't that useful if you rarely take your laptop outside.

The xorg.conf is as follows:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```I've also tried turning off desktop effects, it actually makes the problem worse. As a last resort I could install Jaunty, with this release I didn't have the problem on an identical laptop.

---

### Post by miech on 2009-11-15
Problem solved :) . I found [this](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/) site, added the extra repo's, updated and it works!

All left to do now is find out how to put the solved tag in front of the topic title.

---

### Post by miech on 2009-11-16
Apparently it was too good to be true. After rebooting the problem persists. Any suggestions?

---

### Post by miech on 2009-11-16
Well, I hadn't done anything that bothers anyway, so I did a reinstall. Problem is solved now. For some apparent reason anything works out of the box this time.

---

