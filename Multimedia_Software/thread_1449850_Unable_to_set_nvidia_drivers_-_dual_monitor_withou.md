---
title: "Unable to set nvidia drivers - dual monitor without proprietary drivers?"
date: 2010-04-08
forum: Multimedia Software
---

### Post by hutxubix on 2010-04-08
Hello,

I have been using ubuntu for quite a long time, and for the first time, I am now unable to set nvidia drivers to work. I have just install ubuntu 9.10 amd64 on an AMD 64 athlong X2 with a GEForce 6500 nvidia card.

The only reason I need the proprietary drivers is to use two monitors.

I am going crazy, I have tested everything I have found on the web. I have tried all the nvidia drivers version, I have tried envyng, ... but nvidia do not work!!

I am trying Xinerama with nv, but it does not work either!!!

Here is my xorg.conf file in which I have tried to use nv driver to set dual monitor. X fails to load and it says that screen 0 is deleted, that devices are found but there are no matches in the config file. Any clue?

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor0"
	VendorName   "SAM"
	ModelName    "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor1"
	VendorName   "HP"
	ModelName    "HPL1925"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection



Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV44 [GeForce 6500]"
	BusID       "PCI:1:0:0"
        Screen      0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card1"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV44 [GeForce 6500]"
	BusID       "PCI:1:0:0"
        Screen       1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier     "Myself Configured"
        Screen      1  "Monitor1" 0 0
	Screen      0  "Monitor0"  1280 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
        Option         "Xinerama"  "true"
EndSection

I generated it with Xorg -configure (because dpkg-reconfigure -phigh xserver-xorg do not seem to do anything at all) and then modified it according to hints I found here at 'ubuntuforums'.

In section "serverLayout", it does not work neither if I write

        Screen      1  "Monitor1" 0 0
	Screen      0  "Monitor0"  1280 0

nor 

        Screen      1  "Screen1" 0 0
	Screen      0  "Screen0"  1280 0

Any idea, please

---

### Post by NT4usB on 2010-04-08
I've had best results with envy if I first choose the option to remove nvidia drivers.
Then the install option.

Have you tried changing Driver "nv" to Driver "nvidia"

---

### Post by hutxubix on 2010-04-09
Hello!!

I tried to remove all the nvidia drivers first and then install with envyng -> crashes

I tried to change 'nv' for 'nvidia' in the xorg.conf file that works for just one monitor ->  crashes

I have continued. I have set up Option "Dualhead" and now both monitors are working, but the Desktop ocuppies both monitors (I want separate displays) and I can say which one is on the left and which on the right (so now, I have them swaped, and it is hard for me to change them)

This is very frustrating, because everything worked with 9.04 32 bits!!!!

There is one strange thing: with to monitors running, 'xrandr -q' gives me this:

```
Screen 0: minimum 640 x 200, current 2560 x 1024, maximum 2560 x 1024
default connected 2560x1024+0+0 0mm x 0mm
   2560x1024      76.0* 
   2048x768       76.0  
   1600x600       73.0  
   1280x480       73.0  
   1280x400        0.0  
   640x400         0.0  
```

So it doesn't see two monitors (I have one VGA and one DVI on a GeForce 6500)

Here is my xorg.conf file in its current state: Any idea please?

```
Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor0"
	VendorName   "SAM"
	ModelName    "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor1"
	VendorName   "HP"
	ModelName    "HPL1925"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection



Section "Device"
        Option     "DualHead" "true"
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV44 [GeForce 6500]"
	BusID       "PCI:1:0:0"
        Screen      0
EndSection

Section "Device"
        #Option     "DualHead"  "true"
	Identifier  "Card1"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV44 [GeForce 6500]"
	BusID       "PCI:1:0:0"
        Screen       1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
        DefaultDepth  24
	SubSection "Display"
		Modes       "1280x1024"
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
        DefaultDepth  24
	SubSection "Display"
		Modes       "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Myself Configured"
	Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" LeftOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
        #Option         "Xinerama"  "on"
        #Option         "Clone"    "on"
EndSection

```

---

### Post by hutxubix on 2010-04-12
Hello again,

Thanks to the advice of people from xorg mailing lists, I tried 'nouveau' and it almost made it. I mean, now I have two different monitors running, just where they shoud be, I can move both the cursor and windows from one to the other, and also if I maximize a window in one monitor, it stays there, so everything Ok. 

The only problem I had left was that my gnome panels were just in the 'wrong' monitor. How could I change it? I had tried everything that has come to my mind, and finally!!!! the obvious, dragging the panels. How? with ALT+right button.

Anyway, here I post my actual 'xorg.conf', if it may help someone (you first have to install 'nouveau' from the repos'

```

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor1"
	VendorName   "HP"
	ModelName    "HPL1925"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
        Option      "Position"  "0 0"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor0"
	VendorName   "SAM"
	ModelName    "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
        Option      "RightOf" "Monitor1"  
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nouveau"
    VendorName     "nVidia Corporation"
    BoardName      "NV44 [GeForce 6500]"
    BusID          "PCI:1:0:0"
    Screen         0
# The following information comes from running 'xrandr'
    Option	   "monitor-DVI-I-0" "Monitor1" #assigns the output DVI-I-0 to Monitor0
    Option         "monitor-VGA-0" "Monitor0" #assigns the output VGA to Monitor1
EndSection


Section "Screen"
    Identifier          "screen0"
    Device              "Device0"
    Monitor             "Monitor1"
    DefaultDepth       24

    SubSection "Display"
        Depth           24
        Modes           "1280x1024"
        Virtual          2560 1024 #note the lack of quotes, this line sets the 'maximum' resolution
    EndSubSection
EndSection


Section "ServerLayout"
	Identifier     "Myself Configured"
	Screen      0  "Screen0" 0 0
EndSection

```

---

