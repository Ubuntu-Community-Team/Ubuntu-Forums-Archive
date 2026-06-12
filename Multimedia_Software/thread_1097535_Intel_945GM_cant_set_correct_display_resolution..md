---
title: "Intel 945GM cant set correct display resolution."
date: 2009-03-16
forum: Multimedia Software
---

### Post by sgtpepperaut on 2009-03-16
having some trouble with:
[PHP]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/PHP]

when i click on "preferences..screen resolution" the correct screen resolution 1600x1050 does not show up. The maximum i can set it there is 1360x768. 

this is the only thing that pretty much keeps me from having Ubuntu as my permantent operating system! PLease guys help me out!

i looked around and there is a mention of the file xorg.conf and i was able to edit the file but all thats in there is:

[PHP]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection[/PHP]

---

### Post by sgtpepperaut on 2009-03-17
bump

---

### Post by overdrank on 2009-03-17
Hi and welcome, have you looked at [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by xc3RnbFO8P on 2009-03-17
You could try to add this:
Section "Device"
Identifier "Configured Video Device"
**Driver "intel"**
EndSection

---

