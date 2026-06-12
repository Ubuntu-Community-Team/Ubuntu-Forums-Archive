---
title: "Old ATI and New Annoyance"
date: 2008-05-23
forum: Multimedia Software
---

### Post by BrandonBan6 on 2008-05-23
Hi Friends,

I am running Ubuntu 8.04 with an ATI Radeon X300 (I can hear the groans!). I realize I am starting here with two strikes of using using an ATI card and it being so old, but I'm optimistic. I'm not after compiz or eye candy here, I just want dual monitors to work at a respectable resolutions (a two second feat in windows). I have installed the driver from ATI available here: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html). Then I ran aticonfig initially configuring my card as a dual head, screen 1 to the right of screen 0. Upon reboot of the session, the display will not come up on either screen. I then restore the copy of xorg.conf file to its original configuration and am left stranded and clueless. Here is my restored xorg.conf file: 

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Any thoughts or directions, or can you point me to another post I may have missed? 

thanks!!!

---

### Post by NT4usB on 2008-05-23
Configuring the setup shouldn't be any more dificult because it's ATi... as long as the card supports it, that is. That part of xorg.conf is pretty generic.
Post the xorg.conf that didn't work and maybe we can tweak it around.

---

