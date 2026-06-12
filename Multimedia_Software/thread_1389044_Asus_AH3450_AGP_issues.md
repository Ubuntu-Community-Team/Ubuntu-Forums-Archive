---
title: "Asus AH3450 AGP issues"
date: 2010-01-23
forum: Multimedia Software
---

### Post by morefeo on 2010-01-23
OS: Ubuntu 9.04

Hi all, I've been using ubuntu for a year or so, I had an ATI Saphire radeon 9250 (AGP) working very well with the open source drivers, showing more than 1500 fps on glxgears with compiz enabled.

I pretended to upgrade my video card to an asus ah3450 (ati hd3450), but, when I installed the propietary drivers with envy or "hardware drivers" it shows me a black screen right after log in, or visual errors like ubuntu logo with strange colors, or just the system freezes.

So, what I did: download drivers from the ati site and install them. Then reboot and everything works fine BUT, the acceleration is extremely poor: glxinfo shows 1200 fps without compiz and 200 with it enabled. I can't play games throught wine (at least, with the other video card I could play them, just...it was extremely slow). This new card is suposed to be much better than the old one.

That's why I'm here requesting help, if it's usefull here's my xorg.conf:
> Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Anything wrong?

Also, my system specifications are:
- AMD Athlon xp3200+
- 512mb ddr 400mhz.
- Powertronics 400w.

Thanks in advance, and sorry for my english.

---

