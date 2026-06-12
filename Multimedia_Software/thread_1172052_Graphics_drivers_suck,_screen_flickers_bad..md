---
title: "Graphics drivers suck, screen flickers bad."
date: 2009-05-28
forum: Multimedia Software
---

### Post by Entity` on 2009-05-28
Before you continue, here are my specs:

HIS Radeon 4850 512MB graphics card
Gigabyte GA-MA790XT UD4P motherboard
AMD Phenom II X3 710 processor
4GB G.Skill RAM (1066MHz @ 9-9-9-24)
500 Watt PSU

I've about tried everything, but my graphics drivers just don't seem to want to behave for me.  Every time I try to use 3D drivers for my system, my system doesn't seem to want to accept them.  The proprietary drivers start this thing where my screen flickers at startup for about 6-7 seconds, then everything is fine until I login, then the screen flickers again for another 6-7 seconds.  When I start winecfg, the screen will flicker for about a half a minute while the whole system slows to a crawl and the system monitor shows that my 3rd cpu pegs out.  Attempting to change the screen resolution causes an outright disaster as the screen will keep flickering indefinitely and the display manager will freeze up, which leaves my system at 1600x1200 all the time.

Installing the catalyst 9.5 drivers will cause the system to fail booting.  Sure, the system will load and all, but when it comes time to show the logon screen, the screen will flicker, some glitch junk will display, then flicker again and repeat the whole process 3 times before locking up completely.

For a while I thought it was a bad xorg.conf file; but that was quickly put out of the way when I saw nothing out of the ordinary.  Then I saw this post about there being something wrong with the mtrr table.  For a while, I dabbled with that, only to find out that it was not the problem.  Sorry for wasting your time HughR.  And so now I am stuck with no idea of what could be wrong.

```
> lspci | grep ATI
00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
```

Thats pretty much the whole lot right there.  If there is anyone who can help I would be very grateful.

---

### Post by kingmoffa on 2009-05-29
My jaunty box also does similar things.

Ati Radeon HD2400 

Screen flickers like crazy and system is slow to respond to anything. When viewing a movie file, starting ati control center. 

Not tried any games / 3D apps.

Using ati fglrx driver 

Xorg.0.log has lots of:



```
(II) fglrx(0): EDID vendor "DEL", prod id 53268
(II) fglrx(0): Using hsync ranges from config file
(II) fglrx(0): Using vrefresh ranges from config file
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
swlDalGetDisplayIndex:ERROR: The number of Active Displays is 0 

```

---

### Post by pkjm17 on 2009-05-31
Hmmmm....I just bought the same motherboard, GIGABYTE GA-MA790X-UD4P AM3/AM2+/AM2 AMD 790X ATX AMD. And got the AMD Phenom II X4 940 Deneb 3.0GHz CPU. I think I'm going to stick with my nvidia 8600 card that I allready have. This motherboard takes DDR2 1600 RAM right?

---

