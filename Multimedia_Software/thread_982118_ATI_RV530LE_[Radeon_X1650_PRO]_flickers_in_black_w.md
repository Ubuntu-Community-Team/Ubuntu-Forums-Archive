---
title: "ATI RV530LE [Radeon X1650 PRO] flickers in black with Radeon opensource driver"
date: 2008-11-14
forum: Multimedia Software
---

### Post by MadeR on 2008-11-14
I have just installed Kubuntu Intrepid Ibex.
Given the fact that fglrx driver does not work, I issued a *X -configure* command, copied the produced file into /etc/X11/xorg.conf and edited it.

Apart from 3d (of course) everything works surprising (for me) well, the only problem is that here and there and now and there, the horizontal bands of the screen flicker in black.

It seems to be a Kwin fault, because when I login in KDM no flickering occurs.
Where can I set sync to v_sync in Kwin4?


Linux triskelion 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

sudo lspci -v
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]                                                                        
        Subsystem: PC Partner Limited Device 0850                               
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16             
        Memory at d0000000 (64-bit, prefetchable) [size=256M]                   
        Memory at e1000000 (64-bit, non-prefetchable) [size=64K]                
        I/O ports at 9000 [size=256]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] AGP version 3.0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0Enable-

01:00.1 Display controller: ATI Technologies Inc RV530LE [Radeon X1650 PRO] (Secondary)
        Subsystem: PC Partner Limited Device 0851
        Flags: 66MHz, medium devsel
        Memory at e1010000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2
```

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
#	Option         "AIGLX" "true"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
#	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
	Load  "record"
	Load  "extmod"
	Load  "xtrap"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option		"XkbOptions"	"eurosign:5,compose:rwin"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Acer"
	ModelName    "AL732"
	Option       "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "DDCMode"            	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "DynamicClocks"      	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV530LE [Radeon X1600/X1650 PRO]"
	BusID       "PCI:1:0:0"
	Option      "XAANoOffscreenPixmaps"
#	Option      "AGPMode" "8"
#	Option      "AccelMethod" "EXA"
#	Option      "ColorTiling" "on"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

#Section "DRI"
#        Mode 0666
#EndSection
```

---

### Post by Yellow Pasque on 2008-11-14
What happens when you use XAA acceleration instead of EXA? Better?

Also, you can try the radeonhd driver, which also supports DRI on your card. Build it from source using: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
Make sure you back up your current xorg.conf first.

---

### Post by MadeR on 2008-11-14
> **Temüjin said:**
> What happens when you use XAA acceleration instead of EXA? Better?

Also, you can try the radeonhd driver, which also supports DRI on your card. Build it from source using: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
Make sure you back up your current xorg.conf first.

Thank you!
I really like having 3d back!

Now I am trying to see if kwin syncs to vertical blanking or not.

---

### Post by MadeR on 2008-11-14
> **Temüjin said:**
> What happens when you use XAA acceleration instead of EXA? Better?

Also, you can try the radeonhd driver, which also supports DRI on your card. Build it from source using: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
Make sure you back up your current xorg.conf first.


I receive the following error:
```
sudo ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal -I m4
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
autoreconf: running: /usr/bin/autoconf
[b]configure.ac:86: error: possibly undefined macro: AC_MSG_WARN
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1[/b]
```

---

### Post by MadeR on 2008-11-14
Update.

After learning about the existance of radeonhd, I installed it from:
deb [http://ppa.launchpad.net/tormodvolden/ubuntu](http://ppa.launchpad.net/tormodvolden/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tormodvolden/ubuntu](http://ppa.launchpad.net/tormodvolden/ubuntu) intrepid main


I modified xorg.conf as follows (adding UseConfiguredMonitor), because instead of the correct 1280x1024 resolution, kdm started in 1360x768!

I installed driconf and set "Syncronization with vertical refresh...) to "Always simchronize with vertical refresh...".

Black flickering is still there. And 3D is really slow.
Any ideas?

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
#	Option         "AIGLX" "true"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
#	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
	Load  "record"
	Load  "extmod"
	Load  "xtrap"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option		"XkbOptions"	"eurosign:5,compose:rwin"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
#	Option	    "Protocol" "auto"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "ACER_AL732"
	VendorName   "Acer"
	ModelName    "AL732"
	Option       "DPMS"
	Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
#	Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "AccelMethod"               # [<str>]
        #Option     "offscreensize"             # [<str>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ignoreconnector"           # [<str>]
        #Option     "forcereduced"              # [<bool>]
        #Option     "forcedpi"                  # <i>
        #Option     "useconfiguredmonitor"      # [<bool>]
        #Option     "HPD"                       # <str>
        #Option     "NoRandr"                   # [<bool>]
        #Option     "RROutputOrder"             # [<str>]
        #Option     "DRI"                       # [<bool>]
        #Option     "TVMode"                    # [<str>]
        #Option     "ScaleType"                 # [<str>]
        #Option     "UseAtomBIOS"               # [<bool>]
        #Option     "AtomBIOS"                  # [<str>]
        #Option     "UnverifiedFeatures"        # [<bool>]
        #Option     "Audio"                     # [<bool>]
        #Option     "HDMI"                      # [<str>]

	Identifier  "Card0"
	Driver      "radeonhd"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV530LE [Radeon X1600/X1650 PRO]"
	BusID       "PCI:1:0:0"

	Option	    "AccelMethod" "exa"
	Option      "DRI" "1"
	Option      "NoRandr" "0"
	Option      "UseConfiguredMonitor" "on"
	Option      "TVMode" "PAL"
	Option      "XAANoOffscreenPixmaps"
	Option      "AGPMode" "8"
	Option      "ColorTiling" "on"
	Option      "monitor-VGA_1" "ACER_AL732"
	Option      "monitor-TV_SVIDEO" "TV"
	Option      "monitor-DVI-I_1/digital" "DVID"
	Option      "monitor-DVI-I_1/analog" "DVIA"
	Option      "RROutputOrder" "ACER_AL732"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "ACER_AL732"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes     "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
```

---

### Post by MadeR on 2008-11-15
New Update.

I formatted again and installed intrepid ibex.

The I added the following repositories:
```
deb http://ppa.launchpad.net/tormodvolden/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tormodvolden/ubuntu intrepid main
```

I issued a "sudo apt-get upgrade && sudo apt-get upgrade".

Then I installed the radeonhd drivers
```
xserver-xorg-video-radeonhd - X.Org X server -- AMD/ATI r5xx, r6xx display driver
xserver-xorg-video-radeonhd-dbg - X.Org X server -- AMD/ATI r5xx, r6xx display driver
```

Reboot in manteinance mode, and opt for root shell.
```

cd /usr/lib/xorg/modules/drivers/
mv radeon_drv.so radeon_drv.so.xyz
X -configure
mv radeon_drv.so.xyz radeon_drv.so
cd /etc/X11
cp xorg.conf xorg.conf.uselessEmpty
cp /root/xorg.conf.new xorg.conf
```

Optional: generate a modeline:
```
cvt width height
``` (note, you may need the -r option)

I modified xorg.conf:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

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
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
	Load  "xtrap"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
        Option      "XkbRules"      "xorg"
        Option      "XkbModel"      "pc105"
        Option      "XkbLayout"     "us"
        Option      "XkbVariant"    "alt-intl"
        Option      "XkbOptions"    "eurosign:5,compose:rwin"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol"     "auto"
	Option	    "Device"       "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "ACER"
	ModelName    "AL732"
# V-freq: 60.00 Hz  // h-freq: 63.73 KHz
        #Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
	#Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
# 1280x1024 59.79 Hz (CVT 1.31M4-R) hsync: 63.02 kHz; pclk: 90.75 MHz
	Modeline "1280x1024R"   90.75  1280 1328 1360 1440  1024 1027 1034 1054 +hsync -vsync

EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "AccelMethod"        	# [<str>]
        #Option     "offscreensize"      	# [<str>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ignoreconnector"    	# [<str>]
        #Option     "forcereduced"       	# [<bool>]
        #Option     "forcedpi"           	# <i>
        #Option     "useconfiguredmonitor" 	# [<bool>]
        #Option     "HPD"                	# <str>
        #Option     "NoRandr"            	# [<bool>]
        #Option     "RROutputOrder"      	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "TVMode"             	# [<str>]
        #Option     "ScaleType"          	# [<str>]
        #Option     "UseAtomBIOS"        	# [<bool>]
        #Option     "AtomBIOS"           	# [<str>]
        #Option     "UnverifiedFeatures" 	# [<bool>]
        #Option     "Audio"              	# [<bool>]
        #Option     "HDMI"               	# [<str>]
	Identifier  "Card0"
	Driver      "radeonhd"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV530LE [Radeon X1600/X1650 PRO]"
	BusID       "PCI:1:0:0"
#        Option      "AccelMethod"        	"exa"
	Option      "DRI"
#        Option      "HPD" "auto|off|normal|swap"
#        Option      "HPD" 			"off"
        Option      "ScaleType"			"scale_keep_aspect_ratio"
	Option      "ForceReduced"		"on"
        Option      "UseConfiguredMonitor" 	"on"
        Option      "monitor-VGA_1"		"Monitor0"
        Option      "RROutputOrder"		"Monitor0"
        Option      "TVMode"			"PAL"

EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
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
	#	Modes		"1280x1024"
	#	Modes		"1280x1024_60.00"
		Modes		"1280x1024R"
		Depth     24
	EndSubSection
EndSection
```


[b]glexgears are really slow, and I receive the following error:
```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
```
Black flickering is still present.[/b]

Any ideas? :(

---

### Post by Yellow Pasque on 2008-11-15
My advice would be to ask on the #radeonhd IRC channel (on freenode.net). I've always gotten great help there.

---

