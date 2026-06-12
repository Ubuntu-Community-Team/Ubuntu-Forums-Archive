---
title: "Just installed Ubuntu and have MASSIVE networking dramas"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by ChrisBlizzard on 2009-12-01
Installed Karmic the other day as a dual boot with Win 7 RC on a Fujitsu Siemens Esprimo Mobile Laptop.

Ethernet card is SiS, Windows has "SiS Ethernet Controller" installed.

Wireless card is Atheros AR5007EG.

In windows, some Virtual WiFi thingey shows up but I'm led to believe thats a Win 7 only device.

MY PROBLEMS:-

1. When using ethernet, Ubuntu connects to my ISP but internet is very slow and pages sometimes hang or fail to load at all. (Checking same pages minutes later with Windows browser shows this is not a DNS or server issue)

2. I can't use the wireless. Ubuntu detects the card, but beyond that I am unable to connect to any WAPs or set up my own adhoc wireless network for sharing the ethernet connection with my girlfriend (or for piggybacking her connection when SHE is plugged into ethernet)

I have been experiencing dissatisfaction with Windows again lately and so am in an Ubuntu-friendly disposition, but as you will no doubt understand, if I can't get these issues resolved, I will be deleting mr Linux partition faster than you can say "Why is it that linux developers don't make things more easy to use, to attract Windows power users over to their side?"

---

### Post by Ghostbear121 on 2009-12-01
Ive found when you have a laptop that has both wired and wireless, it will use the wireless by default (if they're both connected). 

Since you wireless technically isn't working, what's happening is your system is trying to run through the wireless.  It fails (after a certain time) and then falls back to wired. 

Check this to see if this is happening:  right-click your network manager, "Disable wireless".  Then open a console (terminal window) and type:
sudo /etc/init.d/networking restart

To restart your wired connection.  It will re-grab a new IP address and register properly on DNS.  Almost certainly this is the issue -- if it is, post back up and we'll get your wireless going.

---

### Post by JBAlaska on 2009-12-02
Just for a start...It's unfortunate that your SiS Mirage 3 card is unsupported by SiS as far as Linux drivers. One of their devs wrote 3d drivers for Linux but is NOT allowed to release them even after hundreds of people contacted SiS and requested they be released.

Here's a [Link](http://ubuntuforums.org/showthread.php?t=615094&highlight=Esprimo) to the thread explaining all this and access to the 2d drivers that do work.

And this [Link](http://lmgtfy.com/?q=Atheros+5007EG+ubuntu) will help you get your wireless working.

Also it never ceases to amaze me how many "windows experts" and "Power Users" have trouble installing Ubuntu while thousands of average users (Including my 72 year old father) have no problems at all...

---

### Post by realzippy on 2009-12-02
Forget that SIS card.

[I]
Dakota tribal wisdom  says that when you discover you are riding a dead horse, the best strategy is to dismount. [/I]

What happened to your NVIDIA card you used on Dapper?

---

### Post by ChrisBlizzard on 2009-12-02
I'm now on a laptop. The SiS card is inbuilt

Details:

Fujitsu Siemens Esprimo Mobile
Ubuntu Karmic
Atheros 5007EG
SiS Mirage 3

Problem summary:

1. Graphics unsupported - stuck on 800x600, no video capability
2. Wireless unsupported - is there any really easy way to get wireless up and running on Linux?

---

### Post by nothingspecial on 2009-12-02
For your wireless try typing ```
sudo modprobe ath5k
```

Worth a go.

---

### Post by realzippy on 2009-12-02
1.All you have to do is moving sis_drv.* to /usr/lib/xorg/modules/drivers/ and modify your Xorg.conf from vesa to sis

2.Seems as you have to compile the patched Atheros driver.Described in given link....

---

### Post by JBAlaska on 2009-12-02
> **ChrisBlizzard said:**
> I'm now on a laptop. The SiS card is inbuilt

Details:

Fujitsu Siemens Esprimo Mobile
Ubuntu Karmic
Atheros 5007EG
SiS Mirage 3

Problem summary:

1. Graphics unsupported - stuck on 800x600, no video capability
2. Wireless unsupported - is there any really easy way to get wireless up and running on Linux?

**Follow the links in my above post and your 2 problems will be solved.**

---

### Post by alegallo on 2009-12-02
Apart from the SIS card, I know there is a bug in network-manager in karmic.

I am having problems too, not depending on my Realtek controller.

---

### Post by ChrisBlizzard on 2009-12-02
For me, this is proof positive that Linux is light-years behind Windows in terms of making things WORK.

Since I have been surfing the net trying to sort problems I have noticed that neither Update Manager nor Software Center work.

This is a joke. It really is.

---

### Post by purct on 2009-12-02
> **ChrisBlizzard said:**
> For me, this is proof positive that Linux is light-years behind Windows in terms of making things WORK.

Since I have been surfing the net trying to sort problems I have noticed that neither Update Manager nor Software Center work.

This is a joke. It really is.

:D....And you trying out linux because? 

let's be clear about this, if Windows is so great then why do user switch to linux?  Don't get me wrong I am not a Microsoft basher(Winders has its uses :P)..but lets face it, everyone has a bad experiences - regardless of what OS they use.....if I had a £1 for every hour wasted on re-build/re-configuring or troubleshooting issues with hardware drivers(regardless of platform, OS or hardware manufacturer) then I would be a very rich man.(ermm... wait a minute, I am a IT Engineer so that can't be right!) :)   

but seriously, I know it can be frustating but its worth spending the time getting the problems resolved. Ubuntu ROCKS!!!

---

### Post by pbrane on 2009-12-02
> **ChrisBlizzard said:**
> For me, this is proof positive that Linux is light-years behind Windows in terms of making things WORK.

Since I have been surfing the net trying to sort problems I have noticed that neither Update Manager nor Software Center work.

This is a joke. It really is.

Most drivers are NOT written by Microsoft. They are written by the device manufacturer. Some companies won't write drivers for the linux kernel for various reasons. One of which is Microsoft not supporting driver development unless it is exclusive to Windows.

I agree that it is a problem. However in all the computers, both laptop and desktop I have only had a problem with Broadcom wireless adapters. At first I used the windows driver wrapped by ndiswrapper. Have you looked at that?

I have a new Dell 1720 (nvidia gfx and intel wireless) everything just worked. And having things mostly work has been my experience with various GNU/Linux distos since 1998. I haven't had Windows installed on any personal computers since then.

Let us know if JBAlaska's suggestions are any help. Good luck.

---

### Post by dajare on 2009-12-02
> **alegallo said:**
> Apart from the SIS card, I know there is a bug in network-manager in karmic.

The problems described in this thread might (or might not!) be related to this bug

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

but it is at least worth checking the work-around suggested in comment #13 in the thread there.

I, too, am new to Ubuntu (first installed the same week 9.10 was released), and am puzzled why the network issues aren't being sorted more quickly. I am, at the moment, happily running 9.04 on an older Tosh Satellite Pro A100, but saw enough of 9.10 to know I would like to upgrade! Unfortunately, the network issue makes that a non-starter. Sigh!

---

### Post by jberkery on 2009-12-02
> **ChrisBlizzard said:**
> 
1. Graphics unsupported - stuck on 800x600, no video capability


Mine came up at 800x600 max resolution too. I found this xorg.conf file on the net somewhere worked for me.



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	VendorName "Unknown"
	ModelName "Unknown"
	HorizSync 31.5-48.5
	VertRefresh 50-70
	# 1024x768 @ 60 Hz, 48.4 kHz hsync
	Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

