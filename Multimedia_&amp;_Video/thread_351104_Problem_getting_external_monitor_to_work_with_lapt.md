---
title: "Problem getting external monitor to work with laptop"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by channel5 on 2007-02-01
Hi

I have an acerr aspire 5100 laptop, It has an external VGA port, but try as I will it will not work correctly with any monitor I plug it into. After scanning a few posts I have collected the information below in the hope that someone with more experience of Xorg.conf can help me.

Thanks



Symptoms
Screen is fine on laptop screen but when connected to external monitor (3 different monitors tried) the monitor does not show the full screen (approx 5% of all the edges are missing), this is also the case when the machine is booting and before it starts X up.

which monitor do you have?
AG Neovo F-419
[http://www.agneovo.com/doc/english/ebrochure/F-419_E-Brochure_V10_20061003.pdf](http://www.agneovo.com/doc/english/ebrochure/F-419_E-Brochure_V10_20061003.pdf)
which graphics card do you have?
ATI Radeon® Xpress 1100 integrated 3D graphics with up to 128MB of shared system memory,
some parts of /etc/X11/xorg.conf -file
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

resolution you want to use
              F-419 should be capable of 1280 x 1024 @ 75 Hz

attached /var/log/Xorg.0.log

---

### Post by sander2 on 2007-04-19
Hi!

I have the same problem when using the ati driver. When I (re)start xorg with my external monitor (DELL FPW 2005 with 1680x150 native resolution) connected to my notebook (Samsung P30 with ATI Mobility Radeon 9200, screen resolution 1400x1050) i get a black screen on the notebook but the external screen shows the right resolution/full screen.

If I connect the TFT AFTER (re)starting xorg I get a screen on both monitors but the the TFT does not show the full screen. like you said, about 5% of the edges on the right and lower side are cut off.

With the fglrx driver i was using with edgy everything was fine. I got the right resolution on my notebook's screen and on the external TFT, even when the external monitor was not connected before (re)starting xorg.

this seems to be a problem with the ati driver. i would really like to use the fglrx driver with feisty, but that doesn't seem to work anymore!

see [http://ubuntuforums.org/showthread.php?t=354592](http://ubuntuforums.org/showthread.php?t=354592)

Can someone please tell me if it is possible to use my external monitor with ati driver the way it worked with fglrx, or even better, if there is/will be a working fglrx driver for ATI mobility radeon 9200 (and below) for feisty?

---

