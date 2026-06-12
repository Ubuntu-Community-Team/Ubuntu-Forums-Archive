---
title: "HOW TO: use external (widescreen) monitor from laptop"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by utdjohn on 2006-09-13
Hey everyone,

My goal is when using my laptop, to send the screen to my new widescreen 19".  I don't care about any fancy dual monitor setups, just the basic "mirroring" or "cloning".  Currently no matter what I do it gets 1024x768, but I want 1440x900.

SETUP:
- Fresh install of Ubuntu 6.06
- Thinkpad T40
- Radeon Mobility M7 LW (7500)
- Viewsonic VA1912wb
- installed [DRI Radeon drivers]("http://dri.freedesktop.org/wiki/") 

ATTEMPTS:
- Found [this page]("http://ozlabs.org/~jk/docs/mergefb/") on mergefb which seems to be what I want.  I duplicated their setup for "mirroring", but no luck.

XORG.CONF:
- two devices, which are the same except in the first one I put the mergefb information, and in the second, I put "Screen 1"
- two monitors
- two screens
- in server layout i put screen 0 -- I think it was Screen 1 but that didn't work at all

> 
Section "Device"
        Identifier      "Radeon 0"
        Driver          "radeon"
        VendorName      "ATI Technologies Inc."
        BoardName       "Radeon Mobility M7 LW"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"        "true"
        Option          "MergedFB" "true"
        Option          "MetaModes" "1024x768-1440x900 1024x768-1024x768"
        Option          "MergedDPI" "100 100"
EndSection

Section "Device"
        Identifier      "Radeon 1"
        Driver          "radeon"
        VendorName      "ATI Technologies Inc."
        BoardName       "Radeon Mobility M7 LW"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"        "true"
        Screen 1	# This refers to second head
EndSection

Section "Monitor"
  Identifier "Laptop LCD"
  Option "DPMS"
EndSection

Section "Monitor"
  Identifier "VA1912wb"
  Option "DPMS"
EndSection

Section "Screen"
    Identifier  "Screen 0"	#Identify screen
    Device      "Radeon 0"	# Device to use
    Monitor     "Laptop LCD"	# Monitor description it will use
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1024x768" 	# First resolution is the default
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "Radeon 1"	# Device to use
    Monitor     "VA1912wb"	# Monitor description it will use
    DefaultDepth 24
    SubSection "Display"
            Depth		24
            Modes		"1440x900" "1024x768" 
    EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen 0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


ERRORS:
- I have attached the Xorg.conf which seems informative.  It is definitely seeing both of my monitors.  The current error it seems to give is:
- It shows all the available modes for both CRT's... on the one I want, it says: 
> (II) RADEON(0): not using default mode "1440x900" (width too large for virtual size)

- Then it skips the mode I want:
> (WW) RADEON(0): Mode "1440x900" is not a supported mode for CRT2
(WW) RADEON(0): 	(Skipping metamode "1024x768-1440x900")
(II) RADEON(0): Merged "1024x768" (1024x768) and "1024x768" (1024x768) to 1024x768 (Clone)
(--) RADEON(0): MergedFB: Virtual width 1024
(--) RADEON(0): MergedFB: Virtual height 768
(++) RADEON(0): MergedFB: DPI set to (100, 100)


I had originally posted this question [here]("http://ubuntuforums.org/showthread.php?p=1489900#post1489900") in a thread which is about the Viewsonic VA1912wb monitor which I have, but I have since decided that my problem is a dual monitor issue.

Thanks in advance!
John

---

### Post by utdjohn on 2006-09-13
Hey everyone,

I thought I would reply with my solutions, since it's always a bummer to have unresolved threads.

My first success came when I used "aticonfig --initial=dual-head".  This got me in the ballpark.

Then, I found this good example xorg.conf from a guy apparently using my same video card at: [http://mg.pov.lt/xorg.conf](http://mg.pov.lt/xorg.conf).  This page has examples of how to do several setups, including the "clone/merged" mode as well as the "big screen" mode.

I'll paste my xorg.conf, which has two setups.  The first and default is one which uses the clone, and gives my VA1912wb its 1440x900.  The LCD scrolls around the window but I'm not using it anyway.  

The other setup is for when I'm not using the external monitor.  I can use this by running "startx -- -layout LCDOnlyLayout".  This is pretty nice!  Probably there's a slick way to give me a menu when booting up, or maybe even autodetect!

Again, as a sidenote, I have installed the DRI Radeon drivers which can be easily found.  I'm not sure if this would work otherwise, but it might.

John

---
Here's the file:

> # 
#
# To run clone on ViewSonic:
#   startx (default)
#   startx -- -layout MergedFB2Layout
#
# LCD Only:
#   startx -- -layout LCDOnlyLayout

#---------------------------------------------------------------------------
# Setup
#---------------------------------------------------------------------------

Section "ServerFlags"
  	Option		"DefaultServerLayout"	"MergedFB2Layout"
# If enabled, lets you deactivate KB/Mouse grabs with Ctrl+Alt+KP_Divide
#	Option		"AllowDeactivateGrabs"	"on"
# If enabled, lets you kill clients that grab the server with Ctrl+Alt+KP_Multiply
#	Option		"AllowClosedownGrabs"	"on"
EndSection


#---------------------------------------------------------------------------
#---------------------------------------------------------------------------
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
EndSection

#---------------------------------------------------------------------------
# Input Devices
#---------------------------------------------------------------------------
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
	Option		"Protocol"		"ExplorerPS/2"
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
  Driver        "wacom"
  Identifier    "stylus"
  # change to /dev/input/event for USB
  Option        "Device"        "/dev/wacom"         
  Option        "Type"          "stylus"
  # Tablet PC ONLY
  Option        "ForceDevice"   "ISDV4"               
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  # change to /dev/input/event for USB
  Option        "Device"        "/dev/wacom"         
  Option        "Type"          "eraser"
  # Tablet PC ONLY
  Option        "ForceDevice"   "ISDV4"               
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  # change to /dev/input/event for USB
  Option        "Device"        "/dev/wacom"         
  Option        "Type"          "cursor"
  # Tablet PC ONLY
  Option        "ForceDevice"   "ISDV4"               
EndSection

#---------------------------------------------------------------------------
# Cloned Display for VA1912wb
#---------------------------------------------------------------------------

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"MergedFB2 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"	"on"
	Option		"MergedFB"	"true"
	Option		"CRT2Position"	"RightOf"
    # This allows X to use MergedFB if the external monitor is not connected
    # when I start X.  The ranges are taken from DDC values of the CTX monitor
    # I use at the office; as listed in Xorg.log.
	Option		"CRT2HSync"	"30-82"
	Option		"CRT2VRefresh"	"50-85"
    # The next line lets me switch between dual-head and several clone modes
    # of varying resolutions with xrandr.
	#Option		"MetaModes"	"1024x768+1440x900 1024x768+1024x768 1024x768-1440x900 1024x768+1280x768 1024x768"
	Option		"MetaModes"	"1024x768+1440x900"
    # A newer version of the radeon driver has an option that disables vertical
    # scrolling for the 1024x768 part.
	Option		"MergedNonRectangular"	"true"
    # In 1024x768-1280x1024 mode the DPI is correct (100), but in all other
    # modes it is weird.  Try to override
	Option		"MergedDPI"	"100 100"
EndSection

Section "Screen"
	Identifier	"MergedFB2 Screen"
	Device		"MergedFB2 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"MergedFB2Layout"
	Screen		"MergedFB2 Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

#---------------------------------------------------------------------------
# Normal LCD Display
#---------------------------------------------------------------------------

Section "Device"
        Identifier      "Radeon 0 (single)"
        Driver          "radeon"
        VendorName      "ATI Technologies Inc."
        BoardName       "Radeon Mobility M7 LW"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"        "true"
        Option          "MergedFB" "true"
        Option          "MetaModes" "1024x768-1440x900 1024x768-1024x768"
        Option          "MergedDPI" "100 100"
EndSection

Section "Monitor"
  Identifier "Laptop LCD (single)"
  Option "DPMS"
EndSection

Section "Screen"
    Identifier  "LCD Screen only"	#Identify screen
    Device      "Radeon 0 (single)"	# Device to use
    Monitor     "Laptop LCD (single)"	# Monitor description it will use
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1024x768" 	# First resolution is the default
    EndSubsection
EndSection


Section "ServerLayout"
	Identifier	"LCDOnlyLayout"
	Screen		"LCD Screen only"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

#---------------------------------------------------------------------------
#---------------------------------------------------------------------------
#---------------------------------------------------------------------------

Section "DRI"
	Mode	0666
EndSection

---

### Post by canonbeck on 2007-07-27
> 
Then, I found this good example xorg.conf from a guy apparently using my same video card at: [http://mg.pov.lt/xorg.conf](http://mg.pov.lt/xorg.conf). This page has examples of how to do several setups, including the "clone/merged" mode as well as the "big screen" mode.


Excellent!!, I copied the whole xorg.conf from that page as is and now everything works on my IBM Thinkpad T40!! 2 heads!, I had no idea that was possible from an old laptop. FYI - The distro I'm using is Mint Cassandra...

---

