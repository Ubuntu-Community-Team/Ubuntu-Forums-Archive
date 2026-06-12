---
title: "IOGEAR External VGA"
date: 2009-04-21
forum: Multimedia Software
---

### Post by wilfred14 on 2009-04-21
Hello - I'm brand new to Ubuntu, and I'm trying to get an external USB VGA card ([http://www.iogear.com/product/GUC2015V/](http://www.iogear.com/product/GUC2015V/)) to work.  I found this thread helpful: [http://ubuntuforums.org/showthread.php?t=260863](http://ubuntuforums.org/showthread.php?t=260863), I used it to set up my xorg.conf as follows at the end of this thread.  

My main monitor is working fine, and it appears my that Ubuntu thinks there is another monitor to the right of my main monitor (I can mouse into the second screen, and move content "off" my second desktop) - but my screen remains black.

I was hoping for some advice on this - I'm willing to accept that the IOGEAR USB is incompatible with Linux, I suppose, but I'd really love to get this working, so I can switch from Windows to Ubuntu... I'm addicted to the multi-monitor layout.  Any help is greatly appreciated.

Here is my xorg.conf:

Section "Device"
	Identifier	"Device[0]"
	Option		"UseFBDev"		"true"
EndSection

Section "Device"
	Identifier "Device[1]"
	VendorName "SiS" # Value does not matter
	BoardName "SiS" # Value does not matter
	Driver "sisusb"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
EndSection

Section "Monitor"
	Identifier "Monitor[1]" #SISUSBVGA
	VendorName "Monitor Vendor" # value does not matter
	ModelName "Monitor Model" # value does not matter
	VertRefresh 50-75
	HorizSync 30-90
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Monitor		"Monitor[0]"
	Device		"Device[0]"
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Monitor		"Monitor[1]"
	Device		"Device[1]"
EndSection

Section "ServerLayout"
	Identifier "Simple Layout"
	Screen 0 "Screen[0]"
	Screen 1 "Screen[1]" RightOf "Screen[0]"
EndSection

---

