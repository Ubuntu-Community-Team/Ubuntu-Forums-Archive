---
title: "ATI Radeon 9000 - Weird resolution problem"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by JasonValdron on 2007-12-30
Hi there,

Just installed a ATI Radeon 9000 due to a video card failure. I have a BenQ FP202W which supports 1680x1050, it gets the right resolution, but it's like if I had a virtual desktop inside, as my Gnome menu bar is set as if I had a 1024x768 screen.

Take a look at the screenshot:
[[img]http://xs122.xs.to/xs122/07520/Screenshot123.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs122&d=07520&f=Screenshot123.png)

And also everything is over-exposed, but you probably don't see it in the screenshot.

Here is my current xorg.conf file:
```

# xorg.conf (xorg X Window System server configuration file)
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
# Removed for forums...
EndSection

Section "InputDevice"
# Removed for forums...
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:8:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"BenQ FP202W"
	Option		"DPMS"
	HorizSync	30-84
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"BenQ FP202W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

Can anyone clarify my problem?
Thanks

---

