---
title: "RADEON7500 64Mb"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by TheBigJimbrowski on 2007-01-10
Hi Ubuntu Gurus,

I have read through a number of posts and I don't think the problems I find there are quite the same as mine..but forgive me if I missed the answer somewhere else.

I am an Ubuntu/Linux newbie, but I am keen to free myself from Microshaft. I am not a windows newbie, and I've been pulling PC's to bits for years.

I have an ATI Radeon 7500 64Mb Video card, which has an S-Video out socket, to which I have  demodulator attached and then the coax to my TV. This set up works fine in WinXP, I can either copy or extend my desktop to the TV quite happily.

In Ubuntu, however, the signal makes it to the TV until X loads (I.E. I get the Bios screen, and then the Ubuntu load screen clearly, then 'fuzz' (I don't know for sure, but my feeling is that the refresh rate is wrong for the TV - the signal is there but not displaying correctly, or perhaps the resolution is too high for it). I assume this is to set somewhere in the xorg.conf, but everytime I edit it, I screw Ubuntu up, it doesn't seem to make any difference which help file I follow I always end up with the 'X Failed to load, check your settings' screen.

Following various forums, help files and even the book Ubuntu Unleashed (for which the Jury is still out - nothing has worked for me yet from the book) I have loaded the XGLRFX(?) drivers as per the instructions (which seem to vary from site to site incidentally) on this site, I have tried setting the DEVICE section DRIVER = "ati", "vesa" and "vba", I have added some things about TV-out, I have installed atitvout, I have read and read the forums but I can't seem to find a solution. Invariably, I have to reset my system at a command prompt with the command the error screen gives you which then resets the video card to defaults. The last time this happened (last night) it didn't even crash to a command prompt, so it looks like another (4th) reinstall *sigh*...

Any ideas what I'm doing wrong? Its really frustrating, I can see that the set up works at boot up, just the second screen (TV) fails when X loads.

This is the ONLY reason why I still have XP on my box, anyone who can help rid me of this evil would surely be in line for spiritual promotion.

Incidentally, I noticed that my Radeon Card's cooling fan is no longer running, so its likely to die soon anyway, any recommendations on Ubuntu compatible cards which /can/ dual screen, one TV on VGA via the S-video port without having to loose too much hair setting it up?

Thanks in advance for any help.

---

### Post by TheBigJimbrowski on 2007-01-10
Sorry - I thought it might help if I posted the relevant xorg.conf entries:

Section "Device"
	Identifier	"Rage 7500 64MB"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Rage 7500 64MB"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Thanks again for your help.

---

