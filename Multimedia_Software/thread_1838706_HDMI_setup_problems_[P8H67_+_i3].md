---
title: "HDMI setup problems [P8H67 + i3]"
date: 2011-09-04
forum: Multimedia Software
---

### Post by allannk on 2011-09-04
Hello guys

Since i'm still pretty green on hardware-setup in Ubuntu, i'd love some help on configuring my new HTPC. 

I got an "old" 32" HD-Ready ([FONT="Courier New"]1360x768[/FONT]) TV which i'd like to use as monitor. Problem is, this TV is not sending the correct data through HDMI. (EDID?)

I tried to manually configure X with different modelines, however i'm pretty sure I got the correct one now. My [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] looks like the following now:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor	"Configured Monitor"
	Device	"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1360x768"
	EndSubSection
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        ModeLine "1360x768" 85.50 1360 1424 1536 1792 768 771 778 795 -Hsync -Vsync
EndSection

```

Is this the right way to configure it? Anyways, I tried restarting gdm but it doesn't change a thing. 

I should probably mention, that most of the time my TV doesn't even display an image at all. When it does, its for a few seconds at a time, with lots of flickering and using just 2/3 of the screen width (with analog TV on the last bit :P). Setting different modelines and restarting X doesn't seem to make any difference, and with the remote desktop, I see that resolution doesn't change at all either. 

Any thoughts?

Thanks in advance. --Allan

---

### Post by BicyclerBoy on 2011-09-04
There have been HDMI bugs with sandybridge graphics, so your monitor may not be to blame.
You could try VGA (DVI-A) connection.

If you use the xorg.conf method you need a device section.
You most likely need horizontal & vertical frequency limits in the monitor section

You can try the xrandr method..
As you have intel graphics checkout this for clues...
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

CVT reduced blanking timing for DVI/HDMI 60Hz.
Modeline "1360x768R"   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync
CVT timing
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

It is very likely that this modes are built into the driver.

---

