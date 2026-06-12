---
title: "Switch from 7900GS -&gt; ATi Rage 128 Pro =&gt; low graphics mode"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by MTiN on 2008-03-10
hello there!
My nVidia 7900GS fan just crashed today so I had to put in a pretty old Rage 128 "XPERT2000" 32mb card. But I didn't manage to get it to work properly! I think I now tried everything I now and simply don't get any further, so pleeeeaaaase help me here!

what I did so far:
set the driver to 'ati' or 'r128', both doesnt work, after a restart I just get "Ubuntu is running in low graphics Mode" and gives me some 800x600 pixel or whatever...
also used sudo dpkg-reconfigure xserver-xorg to reconfigure everything and let everything on default and that didn't help neither...sometime during my hurge amoutn of trial'n'error testing I couldnt even login anymore, it just threw me back directly to the "login:" field...only failsafe gnome worked - and this time in full 1280x1024! But that was no solution, played around a bit longer and now its all crashed again - I think I now enabled the vesa driver, but now as soon as the login screen comes up my display gets black and shows me some message like "unsupported resolution/frequenzy"...so well that was no good decision either..please, someone, helpe me out of this huge mess -.-

---

### Post by MTiN on 2008-03-11
please, I need some help here!

just removed the xorg.conf and let it do everything automatically via
sudo dpkg-reconfigure -phigh xserver-xorg

this is the result:
> Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Rage 128 Pro Ultra TF"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 Pro Ultra TF"
	Monitor		"SyncMaster"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

when I boot up, it first looks good, the login screen runs fine (no "low graphics" message) at 1280x1024...
But when I login, the screen first just gets so yellowish/orange (the background color of the login screen) and stays like that for about 20 seconds, then I get back to the login prompt!
I'm writing this right now via "Failsafe GNOME" selected in the sessions menu at the login screen. 

Whats going on here?

---

### Post by MTiN on 2008-03-12
please, someone help me!

---

