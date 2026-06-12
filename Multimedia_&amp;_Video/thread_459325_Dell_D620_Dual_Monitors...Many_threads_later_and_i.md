---
title: "Dell D620 Dual Monitors...Many threads later and in despair"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by bpickel on 2007-05-30
So ! Here we go. I have been at this for a month or better with little success. I have been issued a new Dell D620 at work and am trying to get dual screens set up. I will list the hardware:

Intel GMA 950
2.0 Gb RAM

I have seen thread after thread on Xinerama etc... and none have worked yet. I have a thinkpad z61m with an ATI X1400 and it has been EASIER than the Intel chip as far a dual screens go.

 
On the Intel chip....I have had no prob getting DRI going and have had no problems with the 1440x900 using the xserver-xorg-video-intel driver instead of i810. I can get cloned output to both screens but not dual head?? Is there an answer? I would love to have both displays at work as I spend alot of time in a terminal server. I prefer Ubuntu enough to deal with one screen, but both would be DARN TOOTIN NICE. So if there is anyone out there with the answer I seek please enlighten me.

This the first thing that has stumped me, I have had to spend sometime but as I have become more familiar with this awesome OS and the forums I find I can accomplish most things and someone must be having success just not this old boy.  

Thanks in advance.

---

### Post by Jim March on 2007-05-30
Add another in abject misery.  I've even tried going back to the i810 driver instead of "intel" and using "915resolution" but NO luck.  I have a late-model Acer with a GMA950 and 1280x800 resolution on the internal LCD.  I could stand driving the external screen in 1024x768 or 1280x1024 (native res) but crap, nothing I've tried works.

"Intel works great!"  Yeah RIGHT.

---

### Post by bpickel on 2007-05-31
It would seem that this would not be such an inconsistent process. Lots have it working others. I have all the rendering going and can use one external monitor just fine. ?

---

### Post by thisllub on 2007-05-31
Post your xorg.conf

---

### Post by bpickel on 2007-05-31
Here it is. As is now. I have DRI and I can use an external monitor but cannot make Xinerama work by following post. Intel should release a control panel. The driver itself couldn't be easier and eyecandy is a breeze. Dual screens is the only hang up


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
	Identifier	"Generic Video Card"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
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

### Post by bpickel on 2007-06-07
I suppose that answers my question. Three weeks no responses. I will wait on a newer driver I suppose. If anyone can help and sees this afters this bump, I'm beggin ya!

---

### Post by JohnnyLee on 2007-06-15
I'm using the i810 driver and have 915resolution installed and am able to get dual head working, but only with 1024x768 on both monitors. Here is my xorg.conf. 

If anyone knows how to get 1440x900 on the laptop monitor, that'd be great. It works in 1440x900 when I only have one screen configured.
```

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
	Option  "XkbOptions"    "ctrl:nocaps"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
  Screen  0
  Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
  Identifier	"dev2"
	Driver		"i810"
	BusID		"PCI:0:2:0"
  Screen 1
  Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#	HorizSync	28-72
#	VertRefresh	43-60
#  DisplaySize 302 191
EndSection

Section "Monitor"
  Identifier  "mon2"
  Option    "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "Screen"
  Identifier  "screen2"
  Device    "dev2"
  Monitor   "mon2"
  DefaultDepth  24
  SubSection "Display"
    Depth   24
    Modes   "1024x768"
  EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0		"Default Screen"
  Screen 1    "screen2" RightOf "Default Screen"
  Option		"Xinerama" "On"
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


```

---

### Post by bpickel on 2007-06-19
I can achieve this as well. The Intel driver seems to much better at monitor auto detection, and also Beryl /Compiz (AIGLX) is much easier. But dual screen FUGEDDEBOUTIT !. You can see that by the lack of responses that the driver isn't there yet. It will work but sporadically. I will keep watching and post a fix asap. Until then back to my trusty IBM Z61m. Thinkpads and Ubuntu are peas in the proverbial pod.

---

### Post by bpickel on 2007-06-19
But by all means please let me know if anyone has any  ideas

---

### Post by JohnnyLee on 2007-06-20
I was able to get it to work using the advice in this post:

[http://ubuntuforums.org/showthread.php?t=425042&highlight=i810+randr]("http://ubuntuforums.org/showthread.php?t=425042&highlight=i810+randr")

---

### Post by veloce on 2007-06-23
Yeah, I'm also browsing occasionally to see if things improve.  

I can't find that anyone has dual monitors working with the "intel" driver.

I'm using the "i810" with "915resolution" on my dell D520 laptop.  (1400x1050 on the laptop, ext screen at 1024x768).

---

### Post by bpickel on 2007-06-29
As we move inexorably toward what we all hope will "Gutsy Greatness" I hope this will be resolved. I am going to give tribe 2 a whirl today and will report if I have any luck.  I get hope from from apps like displayconfig-gtk. It looks like what I need but does not work. The "intel" driver doesn't support xinerama, but does all else much easier. The "i810" gives us xinerama but we have to hack the bios for most widescreen reolutions. This is the double edged sword of open development. These limbo situations happen but they do get resolve.

PS Apologies for the rant, I now this a support category but hey , it is pertinant !

---

### Post by jdr00ejr on 2007-09-10
I'm suffering the same thing.  Thought I'd bumpt this to see if any of the original posters can help me get dual monitors working.

---

