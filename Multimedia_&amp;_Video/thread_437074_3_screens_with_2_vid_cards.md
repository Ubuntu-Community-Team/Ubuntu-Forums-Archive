---
title: "3 screens with 2 vid cards"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by RKETR on 2007-05-08
These forums helped me figure out how to set my video stuff up so I figured I'll post my setup for those that might wanna look at it.

Here's the scoop:
running a Dell GX620 with an onboard Intel i810 based video card (model 82945G/GZ) that will control the left most monitor.  Added a NVidia GeForce FX5200 dual headed video card that will control the right two monitors.  Have all 3 heads attached to 19" NEC LCD2080UX+ flat screen monitors.

Installed Ubuntu 7.04 and started fixin from there...

The end result has Xinerama running with Twinview.  

Twinview handles the dual head NVidia and Xinerama adds the third monitor.

Here's the xorg.conf file:
```

# 5.8.07 - Rob - Added device information for support of second video card
#                objective is to have the system support 3 monitors...
#

Section "Files"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "GeForce FX5200"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
        Option          "TwinView"               "True"
        Option          "TwinViewOrientation"    "LeftOf"
        Option          "MetaModes"              "1600x1200, 1600x1200"
EndSection

Section "Monitor"
        Identifier      "Left LCD2080UX+"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Right LCD2080UX+s"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Left Screen"
        Device          "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Monitor         "Left LCD2080UX+"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1600x1200"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Right Screens"
        Device          "GeForce FX5200"
        Monitor         "Right LCD2080UX+s"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1600x1200"
        EndSubSection
EndSection

# 5.8.07 - Rob - NOTE: Left screen is on onboard Intel video card and right two screens
# are on the dual-headed NVidia card.  TwinView is running the dual head and Xinerama
# adds those to the mix thereby enabling all three screens.
Section "ServerLayout"
        Identifier      "Three Screen Layout"
        Screen          "Left Screen" LeftOf "Right Screens"
        Screen          "Right Screens"
        Option          "Xinerama"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

There ya go...hopefully this can help others out as well...

:guitar:    :popcorn: :-({|= =D>

---

### Post by Nythain on 2007-05-08
thats a pretty groovy setup, definately bookmarking this thread in case i stumble upon an AGP video card cheap, right now running dual monitor on on pic fx5200 or 5500, cant remember

---

### Post by Knowles on 2007-05-09
Twinview? I personally do not like it with 3 monitors, it's more 'inflexible' a better way of doing it is like this:

I have 2 7600gt's

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
	Option		"XkbLayout"	"gb"
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

#############################GRAPHICS#############################

Section "Device"
    Identifier  "7600gt0-0"
    Driver      "nvidia"
    BusID       "PCI:5:0:0"
    Option	"NoLogo"		"On"
EndSection

Section "Device"
    Identifier  "7600gt0-1"
    Driver      "nvidia"
    BusID       "PCI:5:0:0"
    Option	"NoLogo"		"On"
    Screen	1
EndSection

Section "Device"
    Identifier  "7600gt1-0"
    Driver      "nvidia"
    BusID       "PCI:4:0:0"
    Option 	"NoLogo" 		"On"
EndSection

#############################MONITOR#############################

Section "Monitor"
	Identifier	"RM170"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

#############################SCREENS#############################

Section "ServerFlags"
     Option "Xinerama" "on"
EndSection

Section "Extensions"
     Option "Composite" "false"
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "7600gt0-0"
    Monitor     "RM170"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "7600gt0-1"
    Monitor     "RM170"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen2"
    Device      "7600gt1-0"
    Monitor     "RM170"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

#############################LAYOUT#############################

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0" 0 0
	Screen		"Screen1" RightOf "Screen0"
 	Screen		"Screen2" RightOf "Screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mailbinoy on 2007-05-12
> **RKETR said:**
> These forums helped me figure out how to set my video stuff up so I figured I'll post my setup for those that might wanna look at it.

Here's the scoop:
running a Dell GX620 with an onboard Intel i810 based video card (model 82945G/GZ) that will control the left most monitor.  Added a NVidia GeForce FX5200 dual headed video card that will control the right two monitors.  Have all 3 heads attached to 19" NEC LCD2080UX+ flat screen monitors.

Installed Ubuntu 7.04 and started fixin from there...

The end result has Xinerama running with Twinview.  

Twinview handles the dual head NVidia and Xinerama adds the third monitor.

Here's the xorg.conf file:
```

# 5.8.07 - Rob - Added device information for support of second video card
#                objective is to have the system support 3 monitors...
#

Section "Files"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "GeForce FX5200"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
        Option          "TwinView"               "True"
        Option          "TwinViewOrientation"    "LeftOf"
        Option          "MetaModes"              "1600x1200, 1600x1200"
EndSection

Section "Monitor"
        Identifier      "Left LCD2080UX+"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Right LCD2080UX+s"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Left Screen"
        Device          "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Monitor         "Left LCD2080UX+"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1600x1200"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Right Screens"
        Device          "GeForce FX5200"
        Monitor         "Right LCD2080UX+s"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1600x1200"
        EndSubSection
EndSection

# 5.8.07 - Rob - NOTE: Left screen is on onboard Intel video card and right two screens
# are on the dual-headed NVidia card.  TwinView is running the dual head and Xinerama
# adds those to the mix thereby enabling all three screens.
Section "ServerLayout"
        Identifier      "Three Screen Layout"
        Screen          "Left Screen" LeftOf "Right Screens"
        Screen          "Right Screens"
        Option          "Xinerama"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

There ya go...hopefully this can help others out as well...

:guitar:    :popcorn: :-({|= =D>

I have a similar setup, but cant get it(the 3rd monitor) to work. Can someone take a look here and suggest something
[http://ubuntuforums.org/showthread.php?t=439382](http://ubuntuforums.org/showthread.php?t=439382)

---

