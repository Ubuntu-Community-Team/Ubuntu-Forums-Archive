---
title: "dapper upgrade stops dual-head from working"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by vlakmire on 2006-07-25
All,

Just upgraded to dapper kernel 2.6.15 from kernel 2.6.12 and my dual-head stopped working...now I only have single head--unless I boot from my 2.6.12 kernel and then everything works again.

Any idea how to get the new kernel talking to xserver the right way?

Summary:  
my xorg.conf works with 2.6.12 kernel
my xorg.conf doesn't work with 2.6.15 kernel (dapper)
WHY? CAN I FIX?

Here is my xorg.conf file:

--------------------BEGIN-------------------
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
# JJC added for xnee
	Load	"record"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Nvidia DVI controller"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	#Option		"UseFBDev"		"true"
EndSection

Section "Device"
	Identifier	"ATI DVI controller"
	Driver		"ati"
	BusID		"PCI:2:1:0"
	#VideoRAM	65536 # AGP Aperture must be at least 64M in BIOS
EndSection
#Section "Device"
#	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
#	Driver		"i810"
#	BusID		"PCI:0:2:0"
#	VideoRAM	65536 # AGP Aperture must be at least 64M in BIOS
#EndSection

Section "Monitor"
	Identifier	"DELL 1701FP"
	Option		"DPMS"
	#HorizSync	30-70
	#VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"ViewSonic VP191b"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"first"
	Device		"Nvidia DVI controller"
	Monitor		"DELL 1701FP"
	DefaultDepth	16
	SubSection "Display"
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
	Identifier	"second"
	Device		"ATI DVI controller"
	Monitor		"ViewSonic VP191b"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		 "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		 "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		 "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		 "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		 "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen "first"
	Screen "second" RightOf "first"
	Option "Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
----------------------END-------------------

Thanks, 
vlakmire

---

### Post by vlakmire on 2006-07-26
it is an ati driver issue.

is the ati display driver installed in kernel 2.6.15?

How to get it ?

Thanks,
vlakmire

---

### Post by vlakmire on 2006-07-27
found a solution...
IT IS A BUG IN XSERVER-XORG shipped with kubuntu 6.06 

see :  [https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/36461](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/36461)

I downloaded the .debs from here: [http://www.r-a-y.org/ubuntu/](http://www.r-a-y.org/ubuntu/)

tried to install them with dpkg -i x*deb

but needed to first install dependency packages (see output of dpkg install--fixed with aptitude install <insert missing packages>)

then tried dkpg -i x*deb and it installed
restarted xserver with prior working xorg.conf and IT WORKS!

Hallelujah--praise God.

Enjoy.
vlakmire

---

