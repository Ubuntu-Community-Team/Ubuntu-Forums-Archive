---
title: "LCD at native resolution not filling screen"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by uzd4ce on 2007-05-08
Sorry for posting yet another "help me fix my LCD resolution" question, but I'm stumped.

I just bought an Envision 22 inch widescreen LCD.  Its native resolution is 1680x1050 at 60hz.  My Dell is using the Intel I810 driver, so I installed the Intel drivers via Synaptic (sudo apt-get install xserver-xorg-video-intel).

That allowed me to choose the proper resolution from the chooser, but when I do, the image does not fill the screen.  Even when using the monitor menus, I cannot get it to fill about four inches of one side of the screen.  

I can tell the image is squished because I drew a square in GIMP, and it definitely looked more rectangle'ish than square.

If I drop it to a lower resolution, it fills the screen fine, but the text gets pretty fuzzy.  

What kinds of things should I check?

Thanks

ps Just in case it helps, here's the video part of my xorg.conf.
Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"G22LWk"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	50-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"G22LWk"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by blackened on 2007-05-08
What sort of connection are you using? DVI or D-SUB (analog)?

If it's D-SUB, then you can try plugging in a modeline.

Open terminal and do this:

```
gtf 1680 1050 60
```

Cut and paste the output of that into the end of the "Monitor" section in xorg.conf.

As an example, here is mine:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection
```

---

### Post by uzd4ce on 2007-05-08
I'm using VGA.  I added the modeline but it didn't make any difference.

This what I added:
# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  	Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

Any ideas on what I should try next?  

Should I just get a new video card?  Could I walk into CompUSA and get a decent card that works well with Ubuntu, for less than $50 or so?

Thanks

---

### Post by blackened on 2007-05-08
This may be a silly question, but did you reconfigure the xserver after you hooked the new monitor up?
I would suggest trying that first.

---

### Post by uzd4ce on 2007-05-08
Yes, I let it autodetect the new monitor, and it shows properly in xorg.conf.

I have it running at 1440x900something now, and it fills the screen, but everything has a slight fuzz or halo.

I've tried the I810 driver, but with that one, it not only fills the screen, but extends about an inch past the screen border.  When I update to the Intel driver via apt-get, then it looks nice and crisp, but just squeezes it horizontally.

How about the video card question?  What's a good, but inexpensive, Linux-friendly card to try?

Thanks

---

### Post by jjordan on 2007-05-09
You didn't say if you had i915resolution installed and running.  If not then it should fix your problem.  if it doesn't then we may need to manually tell i915resolution what to do.

Just install it and reboot first.  Hopefully that will solve the problem, if not post back for some more help or search the forums there are many many threads about this issue.

-j

---

### Post by stchman on 2007-05-09
> **blackened said:**
> This may be a silly question, but did you reconfigure the xserver after you hooked the new monitor up?
I would suggest trying that first.

How do you reconfigure xserver?  I did some googling and found this:

sudo dpkg-reconfigure xserver-xorg

Is that the proper way?

Thanks.

---

### Post by uzd4ce on 2007-05-09
> **jjordan said:**
> You didn't say if you had i915resolution installed and running.  If not then it should fix your problem.  if it doesn't then we may need to manually tell i915resolution what to do.

Just install it and reboot first.  Hopefully that will solve the problem, if not post back for some more help or search the forums there are many many threads about this issue.

-j

I tried that first, but it didn't seem to work.  I forget what the problem was at that stage though.  Then I read that i915Resolution shouldn't be needed with Feisty, so I uninstalled it.

In any case, last night I went out and bought a GeForce 7300something and everything works fine now.

It also solved some other problems I was having playing large .mp4s, so I'm glad I got it.

Thanks

---

### Post by blackened on 2007-05-09
> **stchman said:**
> How do you reconfigure xserver?  I did some googling and found this:

sudo dpkg-reconfigure xserver-xorg

Is that the proper way?

Thanks.

Yes that's the proper way.

> **uzd4ce said:**
> I tried that first, but it didn't seem to work.  I forget what the problem was at that stage though.  Then I read that i915Resolution shouldn't be needed with Feisty, so I uninstalled it.

In any case, last night I went out and bought a GeForce 7300something and everything works fine now.

It also solved some other problems I was having playing large .mp4s, so I'm glad I got it.

Thanks

Glad to hear you got it sorted out, even though you did have to resort to another card.

---

