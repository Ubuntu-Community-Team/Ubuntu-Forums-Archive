---
title: "Dual Monitor Problem.  ATI 8500 + Matrox G400/450"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by bbskeelz on 2007-03-02
I have two monitors connected to two video cards, 

PCI 1:0:0  (ATI 8500)
PCI 3:0:0  (Matrox G400)

My problem is that I can get either card working, depending on which device I load first.  The second card will get the following message in the log.

(WW) MGA: No matching Device section for instance (BusID PCI:3:0:0) found
(--) Chipset mgag400 found.

Here is a segment of my Xorg.0.log.

Anyone else have had this experience?  Please help if possible, Thanks!

sc.

> II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag400, mgag550
(II) Primary Device is: PCI 03:00:0
(II) ATI:  Candidate "Device" section "ATI RADEON 8500LE".
(II) ATI:  Shared non-ATI VGA in PCI/AGP slot 3:0:0 detected.
(--) Chipset ATI Radeon 8500 QL (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfd6fb000 - 0xfd6fbfff (0x1000) MX[B]
	[5] -1	0	0xfd6fc000 - 0xfd6fc7ff (0x800) MX[B]
	[6] -1	0	0xfd6fcc00 - 0xfd6fccff (0x100) MX[B]
	[7] -1	0	0xfd6fd000 - 0xfd6fdfff (0x1000) MX[B]
	[8] -1	0	0xfd6fe000 - 0xfd6fefff (0x1000) MX[B]
	[9] -1	0	0xfd6ff000 - 0xfd6fffff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xfeb00400 - 0xfeb005ff (0x200) MX[B]
	[12] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[13] -1	0	0xfeb00800 - 0xfeb00bff (0x400) MX[B]
	[14] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[15] -1	0	0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
	[16] -1	0	0xfd800000 - 0xfdffffff (0x800000) MX[B](B)
	[17] -1	0	0xfe6fc000 - 0xfe6fffff (0x4000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[19] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[20] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[24] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[26] -1	0	0x0000cc80 - 0x0000cc9f (0x20) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(WW) MGA: No matching Device section for instance (BusID PCI:3:0:0) found
(--) Chipset mgag400 found

part of my xorg.conf

> Section "Device"
	Identifier	"ATI RADEON 8500LE"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 0
EndSection

Section "Device"
	Identifier 	"Matrox G450"
	Driver 		"mga"
	BusID 		"PCI:3:0:0"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"DELL 17"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"DELL 15"
	Option		"DPMS"
	HorizSync	31-60
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Right Screen"
	Device		"ATI RADEON 8500LE"
	Monitor		"DELL 17"
	DefaultDepth	24
	SubSection 	"Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Left Screen"
	Device		"Matrox G450"
	Monitor		"DELL 15"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Right Screen"
	Screen 1	"Left Screen" LeftOf "Right Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option "Xinerama" "true"
EndSection

---

### Post by bbskeelz on 2007-03-02
Still looking for help on this.  anyone with similar experience and solution?

sc

---

### Post by imluxwhoru on 2007-03-18
Hey. I believe if you take the 
> Option "Xinerama" "true"
tag out of your ServerLayout section (or just comment it out), both monitors should kick on. I've been struggling with this problem myself. I'm trying to get Beryl to work on a 2 video card dual monitor setup. As long as Xinerama is off, both monitors work just fine, but I can't manage to get Beryl up without it. 

Anywhooo. Try turnin' it off. It worked for me. So, your ServerLayout would look like....
> Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Right Screen"
Screen 1 "Left Screen" LeftOf "Right Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
# Option "Xinerama" "true"
EndSection

Oh, and if that does not work, post your full xorg.conf here, as there may be something up with your -Section "Module"- section

Good Luck!

---

### Post by Tankerdog2002 on 2008-03-22
How I got Beryl working with a Matrox 450 dual.

I had the same problem and looked all over the net for answers. All I got for my efforts were a black screen or some kind of fuzzy/grainy garbage when activating Beryl.

I'm not a pro at Linux-Geeking but I did manage to get beryl working with on an old HP xw6000 with Matrox 450.This is not a proven method; however, I reasoned that gaming software must have libraries that support 3D graphics. So I decided to load a bunch of games, ... games that I will probably never use. 
First I ran the standard: [sudo apt-get update], [sudo apt-get upgrade], [sudo apt-get dist-upgrade]. 
Then I installed Adept Package Manager so I couldn't really mess-up my machine much while loading software that I don't know much about.
 
I then loaded a ton of games like GL117, Flight Gear, enigma, xpilot, .....yada...yada...yada

I requested installs with Adept Manager for all my X11, X0rg, X server...blah...blah....blah

The next step is going to sound weird but I kept loading games until I could execute and play GL117 and Enigma. Both of these games would not work after installing them. They always only worked after I loaded more games and games and games. I don't know how much or which ones had the necessary lib files, just a lot until I could execute  and run GL117 and/or Enigma. (I only tinkered with this through about 17 re-installs before I figure out that if GL117 and Enigma are working then my Beryl would work too) I loaded KDEgames but not KDEgames4. KDEgames4 'Borked' my system with broken pipes and I had to reinstall.

I then loaded compiz debian and Gnome manager for compiz;  since I use Linspire/Ubuntu 7.4 Feisty I found that I could not run Beryl without compiz loaded even though I don't use the Gnome Compiz Manager.  In fact it wouldn't work if I enabled the Gnome Manager, but it didn't work for me if I didn't install it either. (Don't ask....I don't know why....It just worked. I even repeated this process afterward just to see if I could repeat it....I did...it worked....I 'dunno why.)

I downloaded Kiba-Dock debian (kiba-dock_0.1-1.2_i386.deb)  
here:   [http://swik.net/kiba-dock](http://swik.net/kiba-dock)


Other versions of Kiba Debian did not work for me. None of that Trevino stuff worked for me, I guess its for newer systems....my system is a real Dino. And I did not edit etc/apt/sources either. This version of Kiba worked without all that. It DID NOT work if I edited etc/apt/sources. Oh...one other thing...you will have to install “libglitz1” first for this Kiba version to work.

I then requested installs with Adept Manager for all Beryl and Beryl dependents. I also installed Emerald.

I know this all sounds weird and I'm not an expert, but this is what I did to get Beryl to work on my 450 Matrox. I hope this helps someone.

Tankerdog2002

---

### Post by Tankerdog2002 on 2008-03-22
Here are some screenshots of my Beryl desktop using the Matrox 450 Dual.

  [http://www.flickr.com/photos/24998276@N08/](http://www.flickr.com/photos/24998276@N08/)

Tank

---

