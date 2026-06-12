---
title: "nvidia 7950 not working with nvidia drivers"
date: 2008-06-18
forum: Multimedia Software
---

### Post by BillGod on 2008-06-18
I recently purchased a 7950gt from a friend.  I had an 8300 in my pc with restricted drivers + compiz...  the works.  Everything has been working fine sine hardy was still beta..  I shutdown and installed the 7950.  I booted up expecting it to just work.. It came up to the 800x600 somethings not right please configure your video settings.  I tried for a couple hours and gave up.  I formated and reloaded.  first boot up.. the "there are restricted drivers available" thing popped up.  I said yes install..  rebooted.. back to the configure your video drivers..  I manually configured the card to use "nvidia" rebooted.. back to the configure your video card window.. I have tried everything. The restricted driver window says its in use.  Here is my xorg.conf

Section "Device"
	Identifier	"Video Device"
	Boardname	"vesa"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Monitor"
	Vendorname	"Dell"
	Modelname	"Dell SE198WFP"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync

	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Video Device"
	Monitor		"Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1280x768@60"
	EndSubSection
EndSection

---

### Post by BillGod on 2008-06-19
i got it working with 1 monitor using the nv driver.  2nd monitor is multi color garbage.  still would like to get nvidia driver working.

---

