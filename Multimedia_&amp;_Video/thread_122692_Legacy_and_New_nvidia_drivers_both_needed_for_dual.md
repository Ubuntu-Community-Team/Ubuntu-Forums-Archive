---
title: "Legacy and New nvidia drivers both needed for dual head system"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by psylo on 2006-01-28
Hi there,

I'm not sure that this is even possible but here goes.

Right I have a dual monitor set up. I have an AGP video card nvidia GeForce FX 5200. I also have a PCI video card, an nvidia RIVA TNT2 64 Pro.

Now I have set up my xorg.conf file nicely, I have dual screen set up with Xinerama so I can drag from one to the other, however when I tried to switch from the default nv drivers to nvidia drivers this is where it all has gone a bit wrong.

In the end I have managed to get one set working using the legacy driver to support the TNT2 card so now on one monitor I am getting full hardware acceleration but I can't get it to work on the other card - purely because if I change the driver in xorg.conf from nv to nvidia it will try to load the old one and I am stuffed as it is not in that set. 

So is there a way of having both sets of drivers co-existing on my system and be able to rename the new ones to something like nvidia-new so in my config file I can call both in and have acceleration on both monitors?

Any help would be greatly appreciated...

Cheers
Andrew

---

### Post by localzuk on 2006-01-28
Please can you post your xorg.conf file for us to poke at?

---

### Post by psylo on 2006-01-28
HI Localzuk.

Thanks for getting back to me. I've removed all the input device gubbins so it isn't too much to wade through.

Section "Module"
	#Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	BusID		"PCI:0:13:0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)"
	VendorName	"NVIDIA"
	Driver		"nv"
	BusID		"PCI:1:00:0"
EndSection

Section "Monitor"
	Identifier	"Compaq MV720"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-85
	Modeline 	"1152x864@75" 107.48  1152 1208 1336 1584   864  864  867  904
EndSection

Section "Monitor"
	Identifier	"Benq FP767-12"
	HorizSync	30-68
	VertRefresh	50-85
	Modeline 	"1152x864@75" 107.48  1152 1208 1336 1584   864  864  867  904
EndSection

Section "Screen"
	Identifier	"Screen Left"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Compaq MV720"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen Right"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)"
	Monitor		"Benq FP767-12"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen Left"
	Screen		"Screen Right" RightOf "Screen Left"
	Option		"Xinerama" "on"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

At the moment I'm uing Xinerama to get the wide screen stuff going, ideally I'd like ti use twinview but am under the impression you need a single card with dual out for that...

Cheers for any help.

Andrew

---

### Post by psylo on 2006-01-30
Hi all,

I'm updating this as it was the weekend when I posted orginally.

I have got acceleration working fine now on one monitor using the legacy drivers and tweaked this is working great. I still can't work out how to get the new drivers loaded in such a way as to not have to uninstall the others though.

any help would be really grateful.

Cheers
AndrewF

---

