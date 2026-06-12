---
title: "s3 trio 63"
date: 2005-10-31
forum: Multimedia &amp; Video
---

### Post by dom on 2005-10-31
the installation (hoary)wouldn't work. It would hang after loading the initrd.gz !!!! and I have a blank monitor with the led flashing (as it does in standby mode).

Eventually I get it to install to work with "expert noquiet"

On reboot, same result. I went into a shell as root (ALT-F1) and logged in and edited /etc/X11/xorg.conf.

I can get the card to work by :
-using 16 as the default depth for the s3 driver
-using the vesa driver

I have not gotten a screen resolution above 800x600 with this card yet. I like to use 1024x768 with this card and monitor (dell 828FI) in other operating systems.

I saw some notes about some drivers in X being dropped with some recent move or upgrade or something, but afaict this card should be working. (aparently it only affects some cards with ramdacs or ramdacs of a certain type).

If anybody else has experience on this one let me know.. If i get it working i will post here.

One of the best advertisments for linux has been, imo, that you can use it on any hardware, especially old stuff, as its generally not too "resource hungry".   

So I don't think we should be losing support for old hardware if at all possible.

---

### Post by Teroedni on 2005-10-31
hmm is it to bad using it in 16 bit??
I think it is possible to get higher than 800x600 in either 16 bit 
or vesa mode

You need to use the modeline generator
here [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)
or here [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

The first one i easier

here is a modeline for 1024x768 at 85 hz generated from the first site

Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

demo of how it may look(note!!: this is from my xorg)
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-110
	VertRefresh	50-150
        Modeline        "1280x1024_100.00"  190.96  1280 1376 1520 1760  1024 1025 1028 1085
EndSection



Then you must probably also add the resolution in section screen. 
Add this to your subsection display at 16 bit
"1024x768@85"


Demo from my xorg file!!!
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024@100" "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Hope this helps

---

### Post by dom on 2005-10-31
thanks a mil Teroedni !

:)

I reverted to the S3 driver, added the modeline at depth 16, and it's looking good.

i wonder does using the 'real' driver give me any performance improvements. Things  seem a little better in more than the look and feel.

here is my monitor segment from xorg.conf :

Section "Monitor"
	Identifier	"DELL 828FI"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-120
	Modeline "1024x768_85.00" 94.39  1024 1088 1200 1376 768 769 772 807	
#	Modeline "1024x768@85"    100.94 1024 1056 1432 1464 768 782 793 807
EndSection


and here is my screen segment (uninteresting depths removed in this paste)

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86c764/765 [Trio32/64/64V+]"
	Monitor		"DELL 828FI"
	DefaultDepth	16
#<snip/>
	SubSection "Display"
		Depth		16
		Modes		"1024x768@85" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768@85" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection

thanks again,

hopefully someday i'll get to depth 24  again (if the work was done for a previous version it should be possible to use it still, i may even give it a lash myself), but for now this is nice. 

dom

---

