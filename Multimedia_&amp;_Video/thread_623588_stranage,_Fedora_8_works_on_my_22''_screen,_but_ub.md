---
title: "stranage, Fedora 8 works on my 22'' screen, but ubuntu 7.10 does not!"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by zhaoshaojun on 2007-11-26
Hi, I am using the latest ubuntu 7.10 version (desktop).  (with updates as Nov 26, 2007)

I recently bought a 22'' wide screen with 1680*1050 resolution.

I have an **intel 865G** onboard video card which does not work. (I have tried everything I can find online. 915resolution, xserver-xorg-video-intel. I did get the 1680*1050 shown up as the resolution option, but everything gets squeezed  (Images look ok, but two sides of the screen are black, any manual/automatic adjusting does not help)

Finally, I tried the **fedora 8 live CD**. To my surprise, it worked out of the box!!!

So, any idea to get the ubuntu gusty 7.10 to work???
Thanks in advance!

-Shaojun

---

### Post by acoustibop on 2007-11-26
My guess is you need to edit /etc/X11/xorg.conf to include your resolution, zhaoshaojun.  My more conventional 1600 x 1200 @75Hz resolution (on a 4:3 19" monitor) works perfectly by default as soon as I install an ATI proprietary driver.

---

### Post by Linteg on 2007-11-26
Have you tried edtiting your xorg.conf? I had to do that to make my laptop's 1680x1050 panel work properly.
```
gksudo gedit /etc/X11/xorg.conf
```
Try to to make your *monitor* and *screen* sections look something like this (don't change the identifiers or device and monitor in the *screen* section though)
```
Section "Monitor"
	Identifier	"Allmän skärm"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Allmän skärm"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1650"
	EndSubSection
EndSection
```

---

