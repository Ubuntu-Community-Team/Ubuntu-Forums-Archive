---
title: "nvidia PCI E 6800 gs can not get it to work. fresh install"
date: 2006-01-23
forum: Multimedia &amp; Video
---

### Post by beerorkid on 2006-01-23
After installing I get a screen that is garbled, it is like I have chosen a resolution that my monitor cannot handle.  I know it can handle 1280x1024

I am on my 10th or so reinstall.  I have tried a bunch of different things.
- installed with frame buffer=false
- edited the horz and vert in xorg.conf
- commented out the DRI in xorg.conf
- put in the modeline a site generator told me to
- selected only 1280x1024 as the only resolution

I am reinstalling to get a good/fresh xorg.conf right now

The computer is a compaq sr1750nx
- ADM 3500
- 2 gb ram
- nvidia 6800 GS PCI-E vid card
- raptor 74gb SATA HD
- monitor viewsonic a90f+

according to this: [http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/](http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/)
my horz sync would be 30-86
vert 50-150
is that correct?

from a modeline generator it would be:
modeline "1280x1024" 85.72 1280 1328 1432 1624 1024 1024 1026 1055

In the bios, which is limited cuz it is a compaq I have chosen the primary video to be PCI-E.  I have no way to disable the onboard besides picking the pci-e as the primary.  Might this be the problem?

I am at a loss on to what to try next.

My friend told me I might have to recompile the kernel to get the agp stuff out.

I will post my xorg.conf here really soon, but was wondering if anybody had any other ideas on what I should post to get this going.

I was so looking forward to getting this going as my main computer and being able to use linux as my main OS.  But it is really bumming me out

Should I install with the onboard video and install nvidia drivers, shut down, install card, and then hope it works?

---

### Post by beerorkid on 2006-01-23
xorg.conf
```
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
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
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41 [GeForce 6800?]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41 [GeForce 6800?]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

it does not seem to have a modeline?  Might inserting it somewhere help?

in the /var/log/Xorg.log  I have:
ww ignoring request to load module GLcore
    so I should comment that out
ww config file hsync 28-64 not yadda yadda
ww config file vsync 43-60 not yadda yadda
    so I will change it to what I had stated above
then a bunch of font BS

---

### Post by beerorkid on 2006-01-23
Allright.  i cannot remember all that I did.  But here is what I remember.
- changed driver to "vesa"
- ran automatix for nvidia drivers
- changed driver to "nvidia"
- and had a bunch of try's that did not work after I used "vesa" to get in.

my xorg now working with 3d
```
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
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
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41 [GeForce 6800?]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-150
#	Modeline "1280x1024" 85.72 1280 1328 1432 1624 1024 1024 1026 1055
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41 [GeForce 6800?]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

while setting up in the install menu, I only chose those two resolutions
I hope this info might help others.

---

