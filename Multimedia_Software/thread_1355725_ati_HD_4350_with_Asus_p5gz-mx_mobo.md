---
title: "ati HD 4350 with Asus p5gz-mx mobo"
date: 2009-12-15
forum: Multimedia Software
---

### Post by enchesss on 2009-12-15
to get this card going in Karmick- 

plug in HD 4350 but do not use yet.

Use on board (intel) and install Karmick

When restricted drivers symbol appears for the ati flgx drivers then click on it and install the propriety flgx drivers BUT DO NOT REBOOT YET

to install xorg open a terminal and run:

```
sudo apt-get install xorg-dev
```

as posted here: [http://ubuntuforums.org/archive/index.php/t-985774.html](http://ubuntuforums.org/archive/index.php/t-985774.html)

to reconfigure xorg for the ati card open a terminal and run:

```
aticonfig --initial
```

I got an error because there was no acceptable "Screen" section in the basic xorg installation above so I copied a 'working' xorg from here:

[http://ubuntuforums.org/showthread.php?t=379569](http://ubuntuforums.org/showthread.php?t=379569)

to edit xorg run:

```
sudo gedit /etc/X11/xorg.conf
```

then paste a working ati file. The one I found that had acceptable ati setting and nearly worked looks like this:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200]"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

but then got another error because the keyboard device section was not acceptable so I deleted these lines:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

```

then re ran
```
aticonfig --initial
```

there were no errors so I rebooted

The ati card now works using dvi cable but I do not get a post or grub because they use the on board drivers. It is a bit of an anxious wait but after 30 seconds the Karmick splash scren appears.

it is not an ideal solution especially if you dual boot. To see the grub menu I need to plug the vga cable into the on board graphics and then just take the cable out or the dvi cable does not work.

If anyone know of a way to get the solution to the card not being able to display the post bios message and grub menu please reply.

---

