---
title: "Help w/ Radeon w/ Dual displays"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by road_rage on 2007-11-20
I just did a clean install of gutsy on my pc and looking to make use of the dual head video. I have been able to install the ATI drive(fglrx) and get it working correctly with compiz, and have read a ton and made it to where I can get the second display to come on after login and allow my cursor to travel to both displays, but it is black. 

I am including my conf if this helps. 

TYIA,

--RR
```

# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "screen1" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "screen1"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
 # 
	Identifier   "monitor1"
	Gamma        1
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
 # 
	Identifier  "device1"
	Driver      "fglrx"
	VendorName  "ATI"
	BoardName   "ATI Radeon (fglrx)"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
 # 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by la1234uk on 2007-11-20
Hi I made it work: I have Ubuntu 7.10, a Radeon 9550 with two monitor.

I can clone the display and I could also set the dual screen desktop like you are trying to do. When I did that few days ago, the screen was not black and everything seemed to work properly. 

However, I do not use that configuration because my second monitor is located in another room (a TV by VGA cable extension and hole in the wall, used to stream movies etc etc)

In this moment I am at work with XP so I cannot post you my Xorg.conf file, I will do that this evening hopefully, in about 8 hours time from now. 

I did all my setting using synaptic and using the Aticonfig command line utility only. What is your Radeon card model ?

Probably you already tried this: you should try to read aticonfig utility help first. Then try the aticonfig --initial switch first and then set one option at a time, to see step by step when/if things go wrong.

Greg

---

### Post by road_rage on 2007-11-21
Thanks for your response. I look forward to seeing you xorg.conf to see if it shows anything that maybe mis-configured. 

Here is the fglrxinfo...
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 XT
OpenGL version string: 2.0.6958 Release

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 XT
OpenGL version string: 2.0.6958 Release

```

I have looked over many posts and many other xorg's, but have yet to see anything that could change this. As this is a new install, to be used as my work desktop, I have tried and tried until I could not longer get x to start and then would re-install gutsy and try again. At this point I have started to customize applications and therefore a bit hesitant to go too "cowboy" on it with trying things. 

I appreciate any information you can offer and anyone else as well. 

TYIA,

--RR

---

### Post by la1234uk on 2007-11-25
Dear road_rage:

sorry I am five days late in answering you. I hope already you solved your problems and your Ubuntu is working properly now.

I attach here my xorg.conf file. It works with my ATI radeon and give me all the compiz functions and dual screen.

Comparing mine and yours, I notice that

- your card BusID is located at PCI:1:0:0 for both devices.
On my xorg.conf I have one at PCI:1:0:0 and the other at PCI:1:0:1. I would try to fix that.
[If you have a XP installation and want to verify, you can go in control panel->system and click the hardware tab, click device manager. in the list of the hardware right-click your card and click properties, you will see the correct PCI:#:#:# address of your card. If you see different numbers try to correct that in your xorg.conf].

- in the section module I have only glx, while you have many other protocols. I would delete those.

- Also I notice that you do not have a section  extra option composite 0 at the end, that may be important.

I would firstly try to modify you xorg.conf with sudo gedit /etc/X11/xorg.conf and experiment with few variations. (backup a working version first).
Also I would use the aticonfig command (available only in terminal command line mode). Read its help and experiment with different dual screen configurations.

If nothing works, I remind you that I made my ATI radeon work only with ubuntu automatic functions.

So I would 

1. reinstall Ubuntu from the CD (I used Ubuntu 7.10), 
2. at that point the ATI card should be inactive, automatically some windows will popup, you should be requested to download the proprietary drivers. In my case I just clicked the window telling me to do so and followed instruction.
3. after reset I went to setup menu-> proprietary hardware and clicked the ATI card driver panel and checked the box and "activate"
4. then after reset it was OK. You may need to adjust resolution, you can do that with the properties->graphics menu.
5. after you do that compiz will be installed but not working. At that point you have to install the xgl. I do not remember the exact commands, just go to synaptic, type xgl in the search and scan the list. You will notice that something like xgl-server, or xgl-session or something like this is NOT installed. 
6. Follow the instruction and install it.

After these steps, everything started to work in my case. All the compiz functions are now working fine, and I enjoy dual screen in clone mode.
I have a ATI radeo card and a 2 years old computer with ASUS motherboard, 1 Gb memory and 3GHz penthium.

Hope this can help. Please do not hesitate to ask for more help if you need. 

Cheers,

Greg Ruo

========

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "jp106"
	Option	    "XkbLayout" "jp,jp"
	Option	    "XkbVariant" "latin,"
	Option	    "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:1"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

======================

---

