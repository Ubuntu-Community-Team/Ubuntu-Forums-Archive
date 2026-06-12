---
title: "Low screen resolution on Dell Latitude C800 laptop"
date: 2008-12-23
forum: Multimedia Software
---

### Post by schwell on 2008-12-23
I have installed Hardy Heron on an older Dell Latitude C800 laptop. The install seemed fine except that the screen resolution is limited to 800x600 and 640x480. I don't need the external monitor support for now but would like the higher resolution supported (1400x1050). 

I have tried checking a number of forum threads and some other Linux support sites and have not found the answer so far.

The graphics card is an ATI Rage Mobility M4 which is recognized by the system: 

lspci -v indicates the following:
...
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP (prog-if 00 [VGA controller])
    Subsystem: Dell Unknown device 00a3
...
so the controller is at least partially recognized.

xorg.conf is the default from the installation which shows:
Section: "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Checking /var/logs/Xorg.0.log showed the following:
(II) Loadmodule: "vesa"
...
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is : PCI 01.00.0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
...

(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 2 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s)
...
Found many modes including several for 1024x768, 1280x1024 and 1400x1050

Then the problem area:
(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using build-in mode "1400x1050" (hsync out of range)
(II) VESA(0): Not using build-in mode "1280x1024" (hsync out of range)
...

It seems that all high resolution modes are prevented because of the hsync levels.

I suspect that the problem is the default hsync range is too low but have no idea how to properly specify it or if the problem is something else.

Any suggestions would be appreciated.

---

