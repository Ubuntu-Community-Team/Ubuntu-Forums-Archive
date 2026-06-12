---
title: "How to get S3 TrioV+ at higher resolution"
date: 2009-09-20
forum: Multimedia Software
---

### Post by WimDBA on 2009-09-20
Hi, 

I have just finished my very first Ubuntu 9.04 installation on a Pentium D PC with a (reused) S3 TrioV+ video card. I can only use it at a 800 x 600 resolution at 60 hz. On Windows XP it worked well with a much higher resolution.

Under Synaptic Package Manager I found that XServer-xorg-video-S3 version 1:0.6.1-1 is installed (selection box marked green).

I have Googled on how to solve this. The answers I get are not clear to me: the S3 card driver is obsolete or wait it is not...  

This is what I found on [xfree.org]("http://www.xfree.org/4.2.0/Status28.html")
> 28. S3
3.3.6: Support (accelerated) for the S3 911, 924, 801, 805, 928, 864, 868, 964, 968, Trio32, Trio64, Trio64V+, Trio64UV+, Aurora64V+, Trio64V2, and PLATO/PX is provided by the XF86_S3 server and the XF86_SVGA server with the s3_svga driver.
> 4.2.0: Support (accelerated) for the 964 (revisions 0 and 1), 968, Trio32, Trio64, Trio64, Trio64V+, Trio64UV+, Aurora64V+, Trio64V2, and PLATO/PX is provided by the "s3" driver (however, only models using the IBM RGB 524, Texas Instruments 3025, or an internal TrioDAC RAMDAC chip are supported). 

Still I'm at a loss. Synaptic says an S3 driver is installed, but it doesn't give me the full ability of this graphics card. I don't know what to do with the information from Xfree.

How should I proceed?

---

### Post by WimDBA on 2009-09-25
I had to spend a while Google-ing and reading the xorg.conf man to find an answer for this old card. With this /etc/X11/xorg.conf file I can now use high resolution:```
Section "Device"
	Identifier	"S3 Trio64V+"
	Driver		"s3"
	Chipset 	"Trio32/64"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"DELL Monitor"
	VendorName	"DELL"
	ModelName	"M770"
	HorizSync	30.0 - 70.0
	VertRefresh	50.0 - 160.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"DELL Monitor"
	Device		"S3 Trio64V+"
	DefaultDepth	16
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection

```I don't know what the
```
 	Option		"UseFBDev"		"true"
```is supposed to do. I noticed no difference when I commented it out. But it is something xorg has put in there herself.

I hope this can help someone.

---

