---
title: "Sample example xorg.conf posted"
date: 2008-09-27
forum: Multimedia Software
---

### Post by davemc on 2008-09-27
While setting up my display I used Ubuntu Forums a lot for tips and techniques, it was great help.

Now I have something that works, I thought I'd give something back and post my complete xorg.conf, since although there a lot of snips on forums, you don't often see a complete, running config file.  

This one is xxorg.conf.2.3, and I keep it in /etc/X11/   Each time I make a change I try to document it, then copy it to xorg.conf ready to run. I call it a different name so apt, dpkg, envy etc can't get at it and wreck it.

It's under constant development of course, so this is just the current version. It works well, and I use this machine all day every day. It's an Asus M2N SLI Deluxe.

This is a pure Xinerama setup, giving seamless three display config. All apps or windows can be dragged across or span any combination of displays. However OpenGL, glx does not work on this arrangement, so consequently it doesnt run as fast as the cards are capable of.

Next thing I plan to add is a Sony projector I've bought as the fourth head, and try twinview, which for nvidia runs quicker.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# Super hand tuned Xorg file by DMc
#
# Currently runs triple display on two dual head nvidia cards
#
# Copyright 2008 McPond Software  
#
#   This file is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   This file is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
# 1.0 Start from base file,  rip out wacom tablet stuff, I dont have one
#     Reorder sections, add dual head setup
#     >>> Gives 
#                Fatal server error:
#                Requested Entity already in use!
# 1.1 Reading further... TwinView mode on nv open source driver
# 1.2 After Feisty upgrade will not start on nVidia, change back to nv
#            until can get it running, then recheck with tools
#            and of course nv doesnt support Twinview?
# 1.3 Add more button support for Razor Copperhead
# 1.4 Envy for Fiesty with help from nvidia-xconfig
# 1.5 Enable dual head again
# 1.6 Change to 20" Viewsonic
# 1.7 Kernel update to 2.6.20 breaks nvidia again. 
#     Change to nv to get started
#     Run envy, then change back to unaltered xorg file
# 1.8 New nVidia 8600GT graphics card with dual DVI output
#     Required latest nVidia drivers 100.41.100
# 1.9 New Samsung SyncMaster 226BW 22" wide screen LCD
# 2.0 Hardy Heron 8.04 major upgrade. New envyng 1.1.1
#     New nvidia installer 173 version
# 2.1 Kernel update 2.6.24-18  Wont start after
#     Disabled two empty font paths, disabled type1 as it wasnt loading
#     Ran envy but boot crashes with Fatal server error Caught signal 4 server aborting libGLcore.so.1
#     Envy only reporting installer v169. It wont do 173 as thats beta
#     Yes, installed 173 manually. Seems 169 does not work on this system
#     Run NVIDIA(blah).run to setup
# 2.2 Add Asus Geforce 7200GS card in second PCI-E 16x slot
#     Needed help from nvidia-xconfig to get both to run
#     The screen IDs are not accumulative, that means, for each physical card, the screen ID starts with 0 again.
#     It treats the 7200 as 'primary' probably because it has a lower bus number
#         meaning you have to login to that screen.  Tool panel can be moved to any screen.
# 2.3 Attempting to get Compiz to run
#         Composite extension not found
#         You must use XOrg >= 6.8 for translucency and shadows to work

#
# Index:
#  ServerLayout
#  Vendor
#  InputDevice - Keyboard
#  InputDevice - Mouse
#  Device - Left
#  Device - Right
#  Monitor - Left
#  Monitor - Right
#  Screen - Left
#  Screen - Right
#  Files
#  Module
#  Extensions
#
#
# Notes:
#  Server Flags must go before Server Layout

# Server layout ties it all together
Section "ServerLayout"
    Identifier     "TripleHeadLayout"
    Screen      0  "CentreScreen" 0 0
    # was rightof, now changed to leftof
    Screen      1  "RightScreen" RightOf  "CentreScreen"
    # Dont use LeftOf Same twice, you get two screens doing the same thing.
    Screen      2  "LeftScreen"  LeftOf   "CentreScreen"
    # Changed this from 0 to 2
    Option          "Xinerama" "On"
    InputDevice    "Ergonomic4000"
    InputDevice    "Razer Copperhead"
EndSection


# Microsoft Ergonomic 4000 Keyboard
Section "InputDevice"
    Identifier     "Ergonomic4000"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
    # Would be nice if the top ribbon web buttons worked
    # and the Zoom slider in the centre
    # and back/forward buttons
EndSection

# Razer Copperhead and KVM based PS2
Section "InputDevice"
    Identifier     "Razer Copperhead"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
        # ZAxis mapping is the scrolling. Exclude from list below
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "9"
    Option         "ButtonMapping" "1 2 3 6 7 8 9"
        # 3 is the wheel click
        # 6 & 7 and 8 & 9 are on the sides of the mouse - and hard to press
EndSection

# Graphics device description
# nVidia GeForce 8600GT    
# Device section is for the video card
# One section per head
Section "Device"
    Identifier     "Left nVidia 8600GT"
    Driver         "nvidia"
# For use after kernel upgrades kills nVidia proprietory
# Also turn off RightScreen
#    Driver         "nv"
    VendorName      "NVIDIA Corporation"
    BoardName       "GeForce 8600 GT"

#   PCI-Express 16x bus
    BusID	   "PCI:7:0:0"
# Appears as PCI:4 on other machines
#     BusID		"PCI:1:0:0"  this is AGP
    Screen          0
        # Options...
EndSection

Section "Device"
    Identifier     "Right nVidia 8600GT"
    Driver         "nvidia"
    VendorName      "NVIDIA Corporation"
    BoardName       "GeForce 8600 GT"
    BusID	   "PCI:7:0:0"
    Screen          1
#        # Options...
EndSection

Section "Device"
    Identifier     "Left nVidia 7200"
    Driver         "nvidia"
    VendorName      "NVIDIA Corporation"
    BoardName       "GeForce 7200 GS"
    # Outer PCI-Express 16x Bus
    BusID	   "PCI:2:0:0"
    Screen          0
#        # Options...
EndSection

# Samsung SyncMaster 226BW - Right
Section "Monitor"
    Identifier     "SyncMaster-226BW"
    VendorName     "Samsung"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
# More Options...
EndSection

# Sony SDM-HS95P - Moved to another machine
#Section "Monitor"
#    Identifier     "SDM-HS95P"
#    VendorName     "Sony"
#    HorizSync       28.0 - 65.0
#    VertRefresh     57.0 - 63.0
#    Option         "DPMS"
# More Options...
#EndSection

Section "Monitor"
	Identifier	"VG2021m"
	Option		"DPMS"
	HorizSync	28-65
	VertRefresh	57-63
        VendorName      "Viewsonic"
# More Options...
EndSection

Section "Monitor"
	Identifier	"SyncMaster-245B"
	Option		"DPMS"
        HorizSync	30-81
	VertRefresh	56-75
        VendorName      "Samsung"
# More Options...
EndSection

Section "Screen"
	Identifier     "CentreScreen"
	Device         "Left nVidia 8600GT"
	Monitor        "VG2021m"
	# Compositing manager
	Option         "RenderAccel" "true"
	Option         "TripleBuffer" "true"
# Not needed on modern X servers	Option         "AllowGLXWithComposite"
	Option         "DPMS" "true"
	DefaultDepth    24
	SubSection     "Display"
		Depth       24
		Modes      "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"RightScreen"
	Device		"Right nVidia 8600GT"
	Monitor         "SyncMaster-226BW"
	# Compositing manager
	Option         "RenderAccel" "true"
	Option         "TripleBuffer" "true"
	Option         "AllowGLXWithComposite"
	Option         "DPMS" "true"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
        # Even though the SyncMaster and the Viewsonic are 1050, the Viewsonic is 10mm taller. Syncmaster has a finer dot pitch, but less physical real estate
EndSection

Section "Screen"
	Identifier	"LeftScreen"
	Device		"Left nVidia 7200"
	Monitor         "SyncMaster-245B"
	# Compositing manager
	Option         "RenderAccel" "true"
	Option         "TripleBuffer" "true"
	Option         "AllowGLXWithComposite"
	Option         "DPMS" "true"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection


# File path names
Section "Files"
# These folders do not exist
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi"
# No files in here    FontPath        "/usr/share/X11/fonts/75dpi"
# removed this tail   /:unscaled"
# No files here either    FontPath        "/usr/share/X11/fonts/Type1"
# path to defoma fonts
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

# Dynamic module loading
Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
# Module does not exist on disk  Load           "type1"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "Extensions"
# Compositing manager for xcompmgr
    Option         "Composite" "Enable"
EndSection


```

---

### Post by andreibranescu on 2009-02-24
Thanks, that helped me.

---

### Post by cob05 on 2009-11-11
Thanks!  Hope this helps me.

---

### Post by dlw on 2010-04-19
I'm trying to set up a 4 monitor sys with 2 different cards.
1 is an ATI, the other an inVidia.

Is this possible?

Will someone help?

Thanks,
dlw

---

