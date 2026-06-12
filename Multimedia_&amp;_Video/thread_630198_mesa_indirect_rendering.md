---
title: "mesa indirect rendering"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by adamb23 on 2007-12-03
Yes, i have an ati radeon 9800 pro graphics card and running gutsy 7.10. the problem im having is when i type this in the terminal glxinfo | grep direct it give me this error. No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

This is a copy of the xorg file

Section "Files"
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
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"DELL 1703FP"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"DELL 1703FP"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"	"true"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
        Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection
Section "DRI"
	Mode	0666
EndSection

I've also tried installing the newest drivers, once through envy the other through the terminal. Any help is appreciated.

---

### Post by ajgreeny on 2007-12-03
I see you have the proprietary fglrx driver installed and would have thought that would be OK for direct rendering, but obviously not.  Just out of interest, try using the open source ati driver and see if you get DR with that.  I use it with my ati 9200SE card without problems at all, even running compiz OK.

Make sure you back up your xorg.conf first, just in case.

---

### Post by acoustibop on 2007-12-03
@adamb23: you probably need to create a symlink for for fglrx driver as part of the installation procedure; unfortunately, apparently Gutsy usually deletes this on booting.

See this extract from the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page"):

> Create the following folder

sudo mkdir /lib/modules/$(uname -r)/volatile

Note: the volatile directory might already exist at this stage then simply continue with the next step.

Create a symbolic link

sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko


NOTE : On my Gutsy install, after a reboot this link was always removed automatically leaving me without an fglrx module loaded, and thus no ATI rendering. There have been several ways of getting around this suggested here, and here is the one that worked for me:

sudo gedit /etc/init.d/ati-module-fix

And put this in it:

#!/bin/sh -e

# For loading ATI display drivers

ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
exit 0


Make it executable

sudo chmod ugo+x /etc/init.d/ati-module-fix

Now, make this run before gdm (which starts with sequence number 13)

sudo update-rc.d ati-module-fix defaults 12

It is possible that gdm sequence number is different. To find the gdm sequence number:

ls /etc/rc2.d/

And substitute 12 in the previous command with gdm sequence number - 1.

I always use their method for installing the current fglrx driver, or use the Restricted Drivers Manager to install the repository fglrx driver.

---

### Post by adamb23 on 2007-12-03
ok i did all that it still says mesa indirect rendering when i check it on the terminal, i seem to have alot of xorg files, would that be a problem?

---

### Post by disturbedite on 2007-12-03
prolly not, as a backup is created whenever you or a system operation (such updating xorg-xserver) occurs.  those are prolly all backups you are seeing.

---

### Post by adamb23 on 2007-12-04
ok any way to uninstall the mesa idr without it affecting all the other programs?

---

### Post by disturbedite on 2007-12-04
if you need it like i do for the intel driver, then no, cuz iirc, a lot of stuff depends on it.
you could open synaptic and find the appropriate mesa package(s) and click on the dependencies tab, then select "Dependents" from the dropdown box.

---

### Post by Chonnawonga on 2007-12-05
acoustibop,

Your fix worked like a charm for me! THANK YOU!

It's strange that that link keeps disappearing. Is this a bug we should be reporting?

Again, thanks!

---

