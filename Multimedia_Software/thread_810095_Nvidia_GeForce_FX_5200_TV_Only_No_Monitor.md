---
title: "Nvidia GeForce FX 5200 TV Only No Monitor"
date: 2008-05-27
forum: Multimedia Software
---

### Post by sharkey77 on 2008-05-27
I have a really old [MediaCenter PC ]("http://support.gateway.com/s/pc/901_Series/2900091/2900091nv.shtml")(2005, Gateway settop box)that is only connected to a TV.  When Ubuntu 8.04 boots I see the splash screen and the text console (CTRL+ALT+F2, etc)show on my TV without issue.  The GUI does not show, just a blank screen.

I saw the guides on enabling dual screens (only have the TV though) but they require access to the GUI.

How do I configure TV out (S-Video) straight from the console?  I won't be able to connect to the internet unless someone also wants to tell me how to install my wi-fi through the console.

Sorry to be a semi-newbie.

Thanks for your help.

---

### Post by Sixten on 2008-05-28
If you're comfortable editing the xorg.conf file, then there are only a couple of options that need to be added for TV-Out to work. The details are in [NVidia's README]("http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-16.html").

The tricky thing is probably the resolutions. For standard NTSC, 800x600 at 60 Hz seems to work well, but things get especially weird when you're trying to output to an HDTV.

---

### Post by sharkey77 on 2008-05-28
I was missing 

> Section	&#8220;Display&#8221;

Modes		&#8220;nvidia-auto-select&#8221;

I had (for anyone else attempting a similar setup)

> Screen Section

Option		&#8221;TVStandard"		 "NTSC-M"
Option 	"UseDisplayDevice" 	 &#8220;TV"
Option 	"TVOutFormat"	 "SVIDEO"

I am now in low res mode and attempting to enhance it.

Thank you.  :)

---

### Post by sharkey77 on 2008-05-28
Cool, selected Nvidia FX generic driver and am running at 800X600 which is perfect for my old 32 inch CRT TeleVision.  Anything higher and the icons get real hard to read (at least in WinXP MediaCenter 2005)

EDIT:  When rebooting I went back to the same problem so I ran the recover console, fixed X, then redid the above changes to xorg.conf.  I am still running at a decent res for a television

---

### Post by sharkey77 on 2008-05-28
Darn, my old wireless card is not found.  I was getting used to Ubuntu just recognizing hardware.  That's a matter for another thread though.

---

### Post by sharkey77 on 2008-06-25
Why does the below xorg.conf work in a fresh Ubuntu 8.4 install but not in a fresh Ubuntu Studio 8.4 install (same computer)?

Studio says that display is an ivalid section name and ignores it as a subsection.





> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option	"TVStandard"	"NTSC-M"
	Option	"UseDisplayDevice"	"TV"
	Option	"TVOutFormat"	"SVIDEO"
EndSection

Section "Display"
	Modes	"nvidia-auto-select"
EndSection

---

