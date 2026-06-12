---
title: "Help with 2 graphics cards"
date: 2006-01-06
forum: Multimedia &amp; Video
---

### Post by somerandomnerd on 2006-01-06
Hi,

Very much a newbie here- just installed Ubuntu (utterly amazed how straightforward it was to get started! From burning an ISO to being online under a new OS in about 15 minutes!) But have got a bit of a problem that I could really use a few pointers with.

My computer is an AMD64, with 2 graphics cards- a Radeon 9800SE in the AGP slot and an nVidia MX4000 in a PCI slot. At the moment, Ubuntu is running entirely on the nVidia's monitor, while the ATI screen is just black with what looks like a CLI prompt in the top left corner (just an underscore sitting there.)

In my "other operating system", I had a desktop that spanned both monitors, and ideally I'd like to get a similar setup going with Ubuntu. (A dual monitor setup is like a mobile phone- you can't go back to life without it!) But after a bit of googling, I realise that's something that has challenged greater minds than mine (I've barely made it out of the GUI so far...) So baby steps...

So what I want to do first is change my monitor from the PCI nVidia card to the AGP ATI card. Changing in the BIOS will change the screen that the bootup info appears on, but either way I end up on the PCI nVidia screen.

If I go into Device Manager, the ATI card is in there, so Ubuntu has obviously detected it's existence and figured out what it is. How do I go about telling it that I want the AGP to be the "real" monitor?

Thanks for reading,


Scott

---

### Post by somerandomnerd on 2006-01-07
Well, I've "solved" the problem...

After playing with the xorg.conf file, I managed to get the display on the screen I wanted it on- however, there were some odd horizontal lines that didn't look healthy. So I installed the ATI drivers from the website via the handy installer program and... borked the xorg.conf file, so I booted into a command line.

I did have the foresight to back up the xorg.conf file, but sadly didn't have the foresight to make a note of how to restore it from the command line.

Rather than boot into my other OS and find out how to do it, I just pulled out the PCi card and reinstalled Ubuntu. Problem solved- albeit in a rather destructive fashion...

All working fine now! Think I'll deal with the dual monitor issue when I've got a better idea what I'm doing!

---

### Post by rittub on 2006-01-07
Could you share your xorg.conf please? I tried to play with it but could not get my second monitor to work. Thanks....

---

### Post by mo_x on 2006-01-08
You have to setup 2 Device sections in your xorg.conf with the appropriate BusId. Also 2 Monitor and Screen sections and put them in the ServerLayout.
If you post details about your configuration, graphics card, monitors, output from lspci etc., I can help create an xorg.conf.

---

### Post by somerandomnerd on 2006-01-08
**rittub**- I'm afraid I've not yet got a dual screen setup working- it's an either/or thing at the moment, and I'm very much feeling my way along at the moment. But I think I'm close...

**mo_x**- any help would be gratefully received!

I've got working xorg.conf files for each monitor working seperately, so I think I'm half way there- what I'm thinking at the moment is that if I change the identifiers of the screens and monitors to "Screen1" and "Screen2" and "Monitor1" and "Monitor2" respectively, then change the relevant "Monitor" element in the "Screen" sections so that each card is pointed at the right monitor, then I'll be half way there.

A bit of googling turned up this thread, which has someone's working xorg.confg file;
[http://www.granneman.com/techinfo/linux/installation/dualheadhowto.htm](http://www.granneman.com/techinfo/linux/installation/dualheadhowto.htm)

I figured that I could just add in his "ServerFlags" section, and edit his "ServerLayout" sections and stick them into the end of my Xorg.conf like this;

```
Section "ServerFlags"
  Option      "Xinerama"  "ON"
EndSection

Section "ServerLayout"
  Identifier  "Dual Head Layout"
  Screen      0 "Screen1" 0 0
  Screen      1 "Screen2" LeftOf "Screen1"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
EndSection
```

Then put the "Device", "Monitor" and "Screen" sections from both of my (independantly) working xorg.conf files into my actual xorg.conf file, then I should be laughing.

This is the "Device", "Monitor" and "screen" sections of my xorg.conf file from my first installation (with a PCI and AGP graphics card plugged in at the time- the installer obviously detected the PCI card and subsequently ignored the AGP card)- before I've edited the screen and monitor identifier to make sure they're unique;

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:0:7:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"Generic Monitor"
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
```


And this is the same sections from my second install, with the PCI card removed so the installer just saw the card in the AGP slot- again, before I've edited the screen and monitor identifier to make sure they're unique;

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 SE (R350 AH)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 SE (R350 AH)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```


The one thing that's stopping me from diving in and giving it a go- how do I make sure that Xinerama is installed and working on my system? I can't find it anywhere in the Synaptic installer, but I gather that it's going to be essential to get an extended desktop across 2 monitors using 2 different graphics cards. Is it just a part of the "X" package?

(I managed to kill my xorg.conf again by trying to enable 3d accelerated graphics through the autoinstaller from the ATI website, so one thing I'm (slowly!) learning is a degree of caution!)

---

### Post by mo_x on 2006-01-08
Xinerama is part of X.
You are on the right track. Make sure the Screen identifiers are matched in the ServerLayout.
Make a backup of your working xorg.conf just in case. You can copy it back on the command line with: sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

---

### Post by somerandomnerd on 2006-01-08
Ace- working fine over 2 monitors!

Many thanks for the help- here's my working xorg.conf file for anyone who it might help out; still need to tweak my screen resolutions and get 3d accelerated drivers working, but those tasks can wait for now!

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies, Inc. Radeon 9800 SE (R350 AH)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"ATI Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 SE (R350 AH)"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:0:7:0"
EndSection

Section "Monitor"
	Identifier	"Monitor2"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"nVidia Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"Monitor2"
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







Section "ServerFlags"
  Option      "Xinerama"  "ON"
EndSection

Section "ServerLayout"
  Identifier  "Dual Head Layout"
  Screen      0 "ATI Screen" 0 0
  Screen      1 "nVidia Screen" LeftOf "ATI Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mo_x on 2006-01-09
Nice :p 
Getting 3d acceleration maybe a problem. I don't know if the nvidia and ati drivers play nice together. nvidia does not use dri. I don't know about ati. You will have to try ;)

---

