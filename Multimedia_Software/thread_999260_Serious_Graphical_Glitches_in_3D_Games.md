---
title: "Serious Graphical Glitches in 3D Games"
date: 2008-12-01
forum: Multimedia Software
---

### Post by SpiritMacardi on 2008-12-01
I'm currently using Ubuntu 8.10 with the ATI FGLRX graphics driver. I've disabled visual effects and tried multiple games, but they all have the same problem: they display a black screen with broken lines of different colors running across.

The sound comes through fine, but the games are unplayable. I've tried with Egoboo and the demo of Penumbra: Black Plague, both of which are native to Linux. If anyone has any suggestions or solutions, I would greatly appreciate it.

---

### Post by IQRules on 2008-12-01
What is your,

$ lspci | grep -i vga

Mind as well post the /etc/X11/xorg.cfg file.

1st time Linux, or upgrade from previous version.

---

### Post by SpiritMacardi on 2008-12-01
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

I'm not a first time user, but I'm not upgraded either. I previously used 64 bit Edgy, but it was too much of a pain so I did a clean install of 32 bit Intrepid.

Edgy displayed 3D graphics just fine, but everything else kept messing up.

---

### Post by SpiritMacardi on 2008-12-01
As for the xorg.conf:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

---

### Post by IQRules on 2008-12-01
Check this,

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by SpiritMacardi on 2008-12-01
> **IQRules said:**
> Check this,

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Just checked. It didn't work.

---

### Post by IQRules on 2008-12-01
> **SpiritMacardi said:**
> Just checked. It didn't work.

Did you do this?

sudo apt-get remove --purge xorg-driver-fglrx

---

### Post by Catalyst2Death on 2008-12-01
sloggerkhan's post here:
[http://ubuntuforums.org/showthread.php?t=651849&page=2](http://ubuntuforums.org/showthread.php?t=651849&page=2)

helped me get it working in hardy/gutsy but they changed stuff in ibex, so it may not work anymore... I think it's still worth trying though...

---

### Post by markbuntu on 2008-12-01
Be really careful with that, many of those are now automatic and others will break x.

---

