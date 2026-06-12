---
title: "Blue Video problem"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by bytejunkie on 2007-05-07
Right, I've searched and read and the general gist seems to be Linux hates ATI...

With that in mind, I'm looking to swap to NVidia, but cant afford just yet. So I could use some suggestions from you guys as to how to fix this issue, if its do-able.

AMD 64 chip, ATI x1950 GPU, Ubuntu Feisty 64 bit.

When I play videos, certain colours appear very blue. In fact Skin Tones are the worst. Will Smith is actually blue in Bad Boys. not cool at all.

I've switched on the ATI Restricted Drivers in Restricted Drivers Manager. This is whats caused the blueness. Unfortunately the only way I can get dual monitors running is to turn that driver on and some trickery in xorg.conf. If i turn the driver off, the blueness disappears.

ANyone got any ideas what this could be?

Matt

---

### Post by bytejunkie on 2007-05-07
need to subscribe to this thread.

---

### Post by Ash1984 on 2007-05-12
I have the same problem. My set up is:

1.86 Core 2 Duo
Gigabyte 965 - S3 (or something)
Sapphire ATI X1950 Pro (512MB PCI-E variant).

Everything works fine in Windows so the card is not faulty. I have flgrx drivers installed with a custom resolution of 1680x1050, though adding the custom resolution was a bit messy. I'm not on the correct computer at the moment so I can't post my xorg.conf contents till later. The problem is videos are all blue, especially skin colour.

Edit: I actually just remembered I opened the same video files in VLC media player and the blue video problem did not occur, however, all sound was messed up (playing random parts of the film).

Could this be a codec problem?

---

### Post by bytejunkie on 2007-05-12
not sure its codecs as i can stop the problem by turning the restricted driver off.

anyone else got any clues to help us?

Matt

---

### Post by Ash1984 on 2007-05-12
This is my xorg.conf:


Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option "DPMS"
	HorizSync	30-83
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen          "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection


I had major problems with getting the resolution 1680x1050 to work on my Dell 2005FPW. In the end I stumbled upon the solution by simply deleting all mode lines which could be causing problems.

---

### Post by Ash1984 on 2007-05-13
Another strange occurrance is when the computer runs for a long time, the graphics card gets very loud. I'm going to try installing the drivers from the ati website.

---

### Post by Ash1984 on 2007-05-13
The blue video problem is solved by installing Totem-xine. I'm not sure what the difference between Gstreamer and xine is but I've had no problems so far.

Next step is to figure out why the ATI restricted drivers cause the graphics cards fan to spin so much!

---

### Post by bytejunkie on 2007-05-13
you're not wrong, that has fixed the blue ness.

now to solve the problem of video hanging the whole pc every so often.

Matt

---

### Post by Nikusan on 2007-05-17
**Blue hue in gstreamer fix: [http://www.mikesplanet.net/2007/05/im-so-blue/](http://www.mikesplanet.net/2007/05/im-so-blue/)**

---

### Post by MaindotC on 2007-12-06
> **Nikusan said:**
> **Blue hue in gstreamer fix: [http://www.mikesplanet.net/2007/05/im-so-blue/](http://www.mikesplanet.net/2007/05/im-so-blue/)**

This definitely fixed my blue problem.  Can you explain why this fixes it?

---

