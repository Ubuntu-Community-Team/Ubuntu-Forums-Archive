---
title: "HDTV resolution problems with Nvidia"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by firedawg24 on 2007-01-23
I have a problem getting the correct resolution for my HDTV which I hook up via DVI. The only resolution I get is 800x600. I have searched all over and done everything that I can but still I have a problem. Part of the problem I believe is under the Nvidia settings GUI it has an option to save current settings to Xorg.conf, it also allows me to view the new Xorg before saving, when I hit save and then open Xorg nothing has changed. If I copy the file and paste  the xorg it crashes when I restart X. My xorg file doesn't show anywhere that it recognizes my TV, only the monitor so I cant figure out where to put modelines or anything else. One more problem is that when I choose seperate X screens and I restart X nothing happens, that is, only the monitor will come on not the TV. It will do twin view that does not require an X restart.  Everytime I restart X is shows the TV as Disabled in the Nvidia settings GUI

Somebody pleeeese help me I am about to chuck my computer out the window.](*,) ](*,) ](*,) ](*,) 

By the way I have an M2npv-vm MOBO with 2 gb of ram, 1 320gb SATA 1-300gb ide and 1500gb ide drives, pchdtv5500 card, running a dual boot MCE/ Ubuntu 6.10 box

---

### Post by fenian on 2007-01-23
You need to edit the xorg.conf file in gedit or nano,editing it rom the nvidia settings doesn't seem to work,at least it hasn't for me.

---

### Post by MetalMusicAddict on 2007-01-23
You are in for some work my friend. ;)

I have a xorg that gives me 1280x720 in Edgy but absolutely flips out in Feisty.

It all comes down to the modline and getting the refresh timings right.

Heres the relevant bits from mine:
```
[SIZE="1"]
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LG TV"
	Option		"DPMS"
	HorizSync       31.5 - 48.5
	VertRefresh     40.0 - 70.0

        # 1280x720 @ 60.00 Hz (GTF) hsync: 44.76 kHz; pclk: 74.48 MHz
	Modeline "1280x720_60.00" 74.48 1280 1336 1472 1664 720 721 724 746 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
	Monitor		"LG TV"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720_60.00"
	EndSubSection
EndSection[/SIZE]
```

Use at your own risk.

---

### Post by firedawg24 on 2007-01-23
> **fenian said:**
> You need to edit the xorg.conf file in gedit or nano,editing it rom the nvidia settings doesn't seem to work,at least it hasn't for me.

What I have done is copy the xorg that nvidia setting gives me and then paste it using nano and it just screws up everything and x wont restart. That part of my problem.

---

### Post by firedawg24 on 2007-01-23
> **MetalMusicAddict said:**
> You are in for some work my friend. ;)

I have a xorg that gives me 1280x720 in Edgy but absolutely flips out in Feisty.

It all comes down to the modline and getting the refresh timings right.

Heres the relevant bits from mine:
```
[SIZE="1"]
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LG TV"
	Option		"DPMS"
	HorizSync       31.5 - 48.5
	VertRefresh     40.0 - 70.0

        # 1280x720 @ 60.00 Hz (GTF) hsync: 44.76 kHz; pclk: 74.48 MHz
	Modeline "1280x720_60.00" 74.48 1280 1336 1472 1664 720 721 724 746 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
	Monitor		"LG TV"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720_60.00"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720_60.00"
	EndSubSection
EndSection[/SIZE]
```

Use at your own risk.

Do you have another monitor hooked up? When I open xorg all it shows is my samsung crt computer moitnor, not my TV.
How do I add the TV settings to the xorg without screwing up X? Can I add another "Monitor" section

---

### Post by MetalMusicAddict on 2007-01-23
Post you xorg, card and desired resolution here.

---

### Post by firedawg24 on 2007-01-23
The card is an on board nvidia Geforce6150 card and I am trying to get 1280x720 or 1312x800, thats what the TV manual says it will support, I wont be home until tomorrow so I cant post the xorg until tomorrow. I will as soon as I get home though.

---

