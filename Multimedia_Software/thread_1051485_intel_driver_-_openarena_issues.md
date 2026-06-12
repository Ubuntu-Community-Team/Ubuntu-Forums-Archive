---
title: "intel driver - openarena issues"
date: 2009-01-26
forum: Multimedia Software
---

### Post by lesemi on 2009-01-26
i installed intrepid fresh and updated all drivers.
I didn't have any issues with this machine when it was on hardy- all programs included openarena worked properly.

i noted after the install that the intel driver didn't work properly - a few days ago - i updated for the patch - but i still see some issues.

the issue with openarena is glitchy - the program start and the game actually works - however it's impossible to see the menus - and during game time it will flash and behave sporatically.  i have saved a screen video - but i can't post it.

here is my lspci

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
02:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem[/PHP]

no need to post xorg.conf - as there is now nothing in there.. no more customization..

thank you for any help

---

### Post by agniruc on 2009-04-12
Have the same problem over here: can't see the menus. If a manage to blindly start the game, it appears to work.

I have also a similar issue with the game Tremulous.

My video entries in the lspci

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by agniruc on 2009-04-25
UPDATE: When installed Jaunty, this issue disappeared.

---

### Post by lariosa42 on 2009-04-25
I have terrible rendering now that I updated to Jaunty.  Int Intrepid, openarena ran really fast.  Now it is so jumpy it is totally unplayable (and I'm not very picky).  Here is some of my lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

And here are the first few lines of glxinfo
```
name of display: :0.0
get fences failed: -1
param: 6, val: 0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

Can anyone help?  I need my OA fix! =)

---

### Post by lariosa42 on 2009-04-28
Just found a fix on [here]("http://renesd.blogspot.com/2009/04/ubuntu-jaunty-half-speed-graphics.html").  I had to modify it slightly (my xorg was in a different place).  This is what I did:

Open the file xorg.config (your might be in a different place than mine) with your favorite text editor using sudo.

```

sudo gedit /etc/X11/xorg.conf

```

Next, find the place that reads
```
Section "Device"
Identifier "Configured Video Device"
EndSection
```
and replace it with
```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "AccelMethod" "UXA"
EndSection
```

restart your computer, and hopefully everything will work.  I'm back to playing OpenArena!  (Still can't get wide-screen, but it runs fast.)

---

