---
title: "Dual-headed display issues with ATI driver"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Horizon88 on 2008-01-08
Hey all.  I've googled around and used a few of the how-to's here which were a big help, but I'm still having problems with this.  I've set up Ubuntu 7.10 here, and I'm trying to get dual monitors to work without cloning.  I have the ATI driver installed properly and I've been browsing tutorials and tinkering with xorg.conf - all day - to see if I can get this working.  I don't seem to be having the same issues as other people have been, so let me lay this out just a bit:

I've currently got two xorg.conf files saved as backups.  With the first one set as xorg.conf, my login manager shows up on one monitor, while the other monitor has an error message saying it can't display that video input type or something along those lines.  When I log in, both monitors display properly with the correct resolutions (1280x1024 on each) but they're cloned.

With the other xorg.conf file I have saved set as default, the login manager displays on the right-hand monitor, and if I mouse to the right side of that monitor and over, it mouses into the left side of the left monitor.  That's backwards, but it's the closest I have so far.  Both of them work with that file with the proper resolutions and such set, even though they're technically backwards (ati-config --desktop=horizontal-reverse or whatever the option is doesn't seem to have any effect  here) but when I log in, it goes to the regular brown background color, hangs for a few seconds, then simply redirects back out to the login manager. :confused: Does anyone know why this is?  I'd really like to fix this so they can run properly without cloning - desktop effects would be nice but I can live without them if I get both monitors working.

Apologies for the lengths, here, but I don't want to leave out any details that may be important. I've never done dual monitors before so I'm a total noob at this part.

The xorg.conf file which logs in but clones displays is:
```

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
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
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
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

And the one which seems to sort of work on dual-display without cloning but doesn't let me log in is:
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "HSync2" "30-82" #This sets the horizontal sync for the secondary display. 
        Option      "VRefresh2" "56-76" #This sets the refresh rate of the secondary display.
        Option      "DesktopSetup" "horizontal"
        Option      "Mode2" "1280x1024"
        Option      "MonitorLayout" "LVDS,LVDS"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Virtual   1280 1024 
                Viewport  0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```
Any help is very much appreciated :)

---

### Post by Yellow Pasque on 2008-01-08
You should have two monitors in your xorg.conf with one having a "left of" or "right of" option.

Try setting it up automatically
```
sudo aticonfig -f --initial=dual-head --screen-layout=(put right or left here depending on where your second screen is located relative to primary monitor).
```

---

### Post by Horizon88 on 2008-01-08
What do I run to find the primary monitor?  It seems to switch back and forth depending on which xorg.conf I use.

---

### Post by Yellow Pasque on 2008-01-08
I'm not sure. Try sudo aticonfig --query-monitor

---

### Post by Horizon88 on 2008-01-09
> 
sudo aticonfig -f --initial=dual-head --screen-layout=(put right or left here depending on where your second screen is located relative to primary monitor).

This command breaks something.  I restarted X and it just showed black screens - I couldn't switch terminals or anything, I had to do a SysRq+SUB and then boot into recovery mode.  --query-monitor (after I export DISPLAY=:0) returns this:
  Connected monitors: crt1, tmds1
  Enabled monitors: crt1, tmds1

---

### Post by Horizon88 on 2008-02-29
I just bought a NVidia card instead.

---

