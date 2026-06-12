---
title: "Display Flickering and Offset; Intel 82830"
date: 2009-11-07
forum: Multimedia Software
---

### Post by badcmpy on 2009-11-07
Hello All:

I've got a panasonic Toughbook CF-28 running Xubuntu 9.10 with all the latest updates. 

After booting the screens flickers and is shifted to the right about an inch wrapping around to the left side of the screen. The splash screen of the mouse looks good but as soon as the login screen loads is when the problem presents.

I can fix the screen if I give it a few minutes and flip between a couple virtual terminals.

I have a minimal xorg.conf but the same problem occurs without it.

Any advice on what might be causing the problem? Is it an Xorg issue? I can post other logs as needed.

The laptop has an Intel 82830 chipset. 

$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)

---

### Post by HighTechRedneck on 2009-11-15
I have been having the exact same problem with my IBM Thinkpad R31 laptop. I know it isn't a problem with the CD, because it runs fine on my Desktop. 

Again, the splash looks fine, but when the desktop loads, the screen flickers and is wrapped around the left hand side. 

Any help would be appreicated.

---

### Post by kusic on 2009-12-03
I have got notebook Acer TravelMate 225X.
It has same Intel 830 chipset and I do have exactly the same flickering problem with Xubuntu 9.10.
The only solution so far is acpi=off boot parameter - flickering and offset is gone.
I know, turning off acpi on notebook is not nice thing, but that all I have found yet.
Jan

---

### Post by kusic on 2009-12-08
Finally, I have found solution!

This is the link where I have found it:

[http://ubuntuforums.org/archive/index.php/t-1307879.html](http://ubuntuforums.org/archive/index.php/t-1307879.html)

***********************************************************************
no need to switch off acpi with acpi=no parameter, just use this one: i915.modeset=0
***********************************************************************
Works great.
Jan

---

