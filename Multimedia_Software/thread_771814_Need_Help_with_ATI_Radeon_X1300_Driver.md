---
title: "Need Help with ATI Radeon X1300 Driver"
date: 2008-04-27
forum: Multimedia Software
---

### Post by jameswendt on 2008-04-27
I have done about 6 or 7 clean installs of Ubuntu 7.04 and keep getting stuck on the video setup.

The video will "work" but it only shows in 640 x 480 mode and if I try to fix it, I end up with a black screen and it's back to reinstalling again.

I have an ATI Radeon X1300 card and a HD LCD screen that will work in up to 1080p mode.

I'd like to simply get this thing to work so that I can get at least 720 HD if not full 1080 (the card should support that mode).

I downloaded the driver from: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I am smart enough to be dangerous (and frustrating) so if you can help walk me through this pretty explicitly, I'm willing to do the work to make it work.

Thank you so much for your help and I hope that we can finally figure this out.

Jim

---

### Post by TheIrishGuy on 2008-04-29
had no problem with 7.04 or 7.10 and x1300.

most likely monitor issues is what your having

heres a copy of my old xorg.conf

run 

sudo cat /var/log/Xorg.0.log | grep Modeline

and grab the modeline to stick into the monitor section that best suits your resolution needs

```

Section "Device"
	Identifier	"x1300"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL E197FP"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
        #Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"x1300"
	Monitor		"DELL E197FP"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"	"57x312"
	EndSubSection
EndSection

```


no doubt your using XGL so the composite section should be disabled

```

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

good luck with hardy, ive yet to get it working

---

