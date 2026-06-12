---
title: "Resolution and no desktop effects on ATI in Gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by landcross on 2007-10-19
Problem: Resolution and no desktop effects on  Gutsy (Reposted as this was unsolved from Development Gutsy Gibbon board which is now closed)


Bush HD LCD TV  via a DVI cable, the ideal screen resolution is 1366x768 @60mhz (32 inch TV)
The best resolution I can get is 1024x768 and lower.
Also  I cannot enable desktop effects.

I am using standard generic Vesa drivers, but the card is a recent ATI.

ATI Radeon X1630 SE.

I have tried the ATI driver found in Restricted Drivers and when using this I have the same 2  problems plus a new one of difficult to read font.
I can hardly read the text when using this driver and still cannot enable display effects or change screen resolution.

Can anyone recommend which ATI driver  I should use for this card.

And how to obtain the required screen  resolution.
The resolution works fine in Windows XP and Vista

this is my third attempt at Ubuntu, Each time I had problems with X  GUI after installing upgrades and could not restore and returned back to using XP (Please give detailed instructions in your reply Thanks)


Notes:
sudo gedit /etc/X11/xorg.conf



Section "Device"

	Identifier	"Generic Video Card"

	Boardname	"vesa"

	Busid		"PCI:2:0:0"

	Driver		"vesa"

	Screen	0

EndSection



Section "Monitor"

	Identifier	"Generic Monitor"

	Vendorname	"Generic LCD Display"

	Modelname	"LCD Panel 1360x768"

	Horizsync	31.5-48.0

	Vertrefresh	56.0 - 65.0

  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync

  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync

  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync

  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync

	Gamma	1.0

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"Generic Video Card"

	Monitor		"Generic Monitor"

	Defaultdepth	24

	SubSection "Display"

		Depth	24

		Virtual	1024	768

		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"

	EndSubSection

EndSection



Section "ServerLayout"

	Identifier	"Default Layout"

  screen 0 "Default Screen" 0 0

	Inputdevice	"Generic Keyboard"

	Inputdevice	"Configured Mouse"

	

	# Uncomment if you have a wacom tablet

	#	InputDevice     "stylus"	"SendCoreEvents"

	#	InputDevice     "cursor"	"SendCoreEvents"

	#	InputDevice     "eraser"	"SendCoreEvents"

EndSection

Section "Module"

	Load		"glx"

	Load		"GLcore"

	Load		"v4l"

EndSection

Section "device" #  

	Identifier	"device1"

	Boardname	"vesa"

	Busid		"PCI:2:0:0"

	Driver		"vesa"

	Screen	1

EndSection

Section "screen" #  

	Identifier	"screen1"

	Device		"device1"

	Defaultdepth	24

	Monitor		"monitor1"

	SubSection "Display"

		Depth	24

		Modes		"640x480@60"

	EndSubSection

EndSection

Section "monitor" #  

	Identifier	"monitor1"

	Vendorname	"Plug 'n' Play"

	Modelname	"Plug 'n' Play"

  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync

	Gamma	1.0

EndSection

Section "ServerFlags"

EndSection

---

### Post by andreeh on 2007-10-19
```
sudo apt-get install xorg-driver-fglrx
```
then
```
sudo aticonfig --initial
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
^-- setup your screen there.

EDIT: And to get the desktop effects you need to run XGL (package is named xserver-xgl) which will enable compiz for you, although you won't be able to get direct rendering. There's several guides on how to get your ATI card working with XGL/Compiz.

Good luck.

---

### Post by landcross on 2007-10-19
thanks for help on item 2, i received this message.

bill@bill-desktop:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

What do I do next? (Or where is the file I need to copy?)


Thanks

---

### Post by landcross on 2007-10-19
**Help Please Urgent**

I have just checked my 

 /etc/X11/xorg.conf

[B]
It is now blank[/B]

Cqan anyone help.

I will leave my PC on until I can get help. As I know I have lost me settings after following this advice in section 1

Help please!

---

### Post by argosreality on 2007-10-19
Whenever you mess with xorg.conf always make a backup first (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup. You can generate a new xorg.conf file with dpkg-reconfigure xserver-xorg which should regenerate a new one for you

---

