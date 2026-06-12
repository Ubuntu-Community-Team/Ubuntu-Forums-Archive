---
title: "Feisty+Ati 8500LE+(S-Video)Tv Out Problems"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by zeep25 on 2007-08-15
I have searched ubuntuforums/google and everywhere else i can imagine.

Let me first try to explain my goal. I got a desktop with ATI Radeon 8500 LE with Ubuntu Feisty. The display works fine on the monitor, I want to be able to duplicate my screen onto my tv using the S-Video out in the ATI card. 

Me, being a first time ubuntu user, let me go over what i have done so far.

**Attempt to install Ati Proprietary/ fglrx drivers:**
[LIST=1]
[*]Following the Ubuntu repositories instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). When i try to open "System -> Administration -> Restricted Drivers Manager", i get a message saying "Your hardware does not need restricted drivers".
[*]Following the Manual ati.com updated driver instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). When i try to run the following command```
bash ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/feisty
```
I get "./ati-installer.sh: 156: Syntax error: Bad substitution" error. Following instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d01742cec183112be090e459b74129606e258f79-3") , i tried 
```
sudo mv /bin/sh /bin/sh.old
sudo ln -s /bin/bash /bin/sh
fakeroot sh ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/feisty
sudo rm /bin/sh
sudo mv /bin/sh.old /bin/sh
```
and i get with this error  "Requested package is not supported."
[/LIST]

**Attempt to get S-Video Out to work:**
I don't know where i got the help/editing from, but i ended up following a bunch of posts from ubuntuguide and a little bit from here and there made it _SORTA_ work for me. I'm gonna post my xorg.conf below. This is what happens with this configuration. I plug in the monitor and the svideo to my tv, turn on the computer, Both screens show everything until the ubuntu bootup screen shows up, then the TV goes blank until the login screen shows. Everything works fine from there. If i do one of the following: restart x server/start any video player (vlc/mplayer/etc), both screens go off and thats it, nothing comes back on. 
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection


Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection


Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection


Section "Device"
	Identifier	"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"TVOutput"	"NTSC"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-50
	VertRefresh	60-60
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection


Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

Now i just want to be able to view what's on myscreen, on my tv and have the ability to watch videos, etc onto the TV :)

p.s. the video card IS supported by [ati's proprietary drivers]("https://www2.ati.com/drivers/linux/linux_8.28.8.html#173867")

Any help, or point to the right direction would be apreciated

---

### Post by tseliot on 2007-08-15
> **zeep25 said:**
> p.s. the video card IS supported by [ati's proprietary drivers]("https://www2.ati.com/drivers/linux/linux_8.28.8.html#173867")
Actually the card WAS supported by ATI.

driver 8.28.8 doesn't work with Xorg 7.2 which Feisty uses. This means you will have to use the open source ("ati") driver. There is no need to install the proprietary driver ("fglrx").

The open source driver doesn't support the TV-OUT though.

If using the S-Video Out really matters to you I'm afraid you'll have to buy a new card (maybe an Nvidia card?)

---

### Post by zeep25 on 2007-08-15
Ohhh ... hmm i see ...

we'll can i use the opensource "ati" drivers to get the s-video out to work? actually it does work with the open source drivers, the xorg.conf (posted in in the first post) works fine, until i start a media player (vlc/mplayer) ... that's when it crashes or something ... 

maybe something i can do to fix that ? something in the xorg.conf ?

If i want to buy a new card, the motherboard (intel d845ebg2) only supports AGP 2x/4x. What card would you recommend that would work with s-video ?

---

### Post by tseliot on 2007-08-16
> **tseliot said:**
> The open source driver doesn't support the TV-OUT though.

I'm quoting myself.

An Nvidia card should be fine (make sure it's at least a geforce 5xxx)

---

