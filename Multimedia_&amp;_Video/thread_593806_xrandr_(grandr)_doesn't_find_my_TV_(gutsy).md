---
title: "xrandr (grandr) doesn't find my TV (gutsy)"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by bohsocks on 2007-10-27
Hello folks.  I recently upgraded to Gutsy.... and I found that my MergedFB setup (My laptop screen and the TV) doesn't work anymore.  I had gotten it to work by editing my xorg.conf file in the following way:

```
Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"AGPMode"		"4"
	Option		"EnablePageFlip"	"on"
	Option		"RenderAccel"		"on"
	Option		"DynamicClocks"		"on"
	Option		"BIOSHotkeys"		"on"
	Option		"MergedFB"		"true"
	Option		"CRT2Position"		"Below"
	Option		"MetaModes"		"1280x800-640x480"
	Option		"MergedNonRectangular"	"true"
	Option 		"MergedXineramaCRT2IsScreen0" "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync    28-64
	Vertrefresh    43-60
EndSection
```

That worked fine in Feisty... but for some reason it doesn't work in Gutsy.  I have found that the "Screens and Graphics" application is pretty much useless.  I looked online and read about using xrandr (and I also installed grandr).... I noticed that xrandr doesn't recognize my TV as being connected at all.  It is connected through a VGA port out the back of my laptop to a box that converts it from VGA to Composite, which goes into the TV.

How do I make it so that xrandr recognizes my VGA connection?  Right now, all I have on my TV is a test pattern.  I want my 2nd screen back :(

---

### Post by motin on 2008-02-13
What is your output from "xrandr"?

If you do not see any TV entry there, I suggest you move away your current xorg.conf file from /etx/X11 and then use the Switch User feature and login as another user. (More info here: [http://ubuntuforums.org/showthread.php?t=679059](http://ubuntuforums.org/showthread.php?t=679059)). This will auto-generate a stock xorg.conf where you can try running "xrandr" again and posting it's output here.

---

