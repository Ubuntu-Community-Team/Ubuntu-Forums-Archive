---
title: "Upgrade to Xorg 7.2 broke Xinerama configuration"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by jvm on 2007-04-21
Hi!

I upgraded Xorg from 7.1 to version 7.2, and my previously perfectly working Xinerama configuration with two TFT monitors connected to one graphic card doesn't work anymore. I used the following xorg.conf, which shows the same image on both monitors now:
(If you've any questions why this configuration file worked and why there are so many screens and devices defined, don't ask me, I just copied and modified it a little...)

```
Section "Module"
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbModel"	"ltcd"
	Option		"XkbLayout"	"de"
	Option "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"	"on"
	Option		"backingstore"	"on"
    	Option 		"AllowGLXWithComposite" "true"
	Option          "XAANoOffscreenPixmaps" "true"
EndSection

Section "Device"
	Identifier	"MergedFB ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"	"on"
	Option		"backingstore"	"on"
    Option "AllowGLXWithComposite" "true"
	Option		"MergedFB"	"true"
	Option		"CRT2Position"	"RightOf"
    # This allows X to use MergedFB if the external monitor is not connected
    # when I start X.  The ranges are taken from DDC values of the CTX monitor
    # I use at the office; as listed in Xorg.log.
	Option		"CRT2HSync"	"30-80"
	Option		"CRT2VRefresh"	"59-75"
    # The next line lets me switch between dual-head and several clone modes
    # of varying resolutions with xrandr.
	#Option		"MetaModes"	"1024x768-1280x1024 1024x768-1024x768 1024x768+1280x1024 1280x1024 1024x768 800x600 640x480"
	Option		"MetaModes"	"1280x1024-1280x1024 1280x1024"
    # My laptop's internal LCD is 100dpi.  The external LCD is designed
    # for 1280x1024, and the picture is streched.  The ati driver computes
    # its DPI by looking at the physical size of the external LCD, and gets
    # ~65 DPI.  I want to override that.
	Option		"MergedDPI"	"100 100"
    # This should speed up RENDER acceleration and perhaps make compositing not
    # so terribly slow.  What it does, is make EVERYTHING slow.
#	Option		"AccelMethod"	"EXA"
	Option          "XAANoOffscreenPixmaps" "true"
EndSection

Section "Device"
	Identifier	"MergedFB2 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"	"on"
	Option		"backingstore"	"on"
    Option "AllowGLXWithComposite" "true"
	Option		"MergedFB"	"true"
	Option		"CRT2Position"	"RightOf"
    # This allows X to use MergedFB if the external monitor is not connected
    # when I start X.  The ranges are taken from DDC values of the CTX monitor
    # I use at the office; as listed in Xorg.log.
	Option		"CRT2HSync"	"30-81"
	Option		"CRT2VRefresh"	"56-76"
    # The next line lets me switch between dual-head and several clone modes
    # of varying resolutions with xrandr.
	#Option		"MetaModes"	"1024x768-1280x1024 1024x768-1024x768 1024x768+1280x1024 1280x1024 1024x768 800x600 640x480"
	Option		"MetaModes"	"1280x1024-1280x1024 1280x1024"
    # A newer version of the ati driver has an option that disables vertical
    # scrolling for the 1024x768 part.
	Option		"MergedNonRectangular"	"true"
    # In 1024x768-1280x1024 mode the DPI is correct (100), but in all other
    # modes it is weird.  Try to override
	Option		"MergedDPI"	"100 100"
	Option          "XAANoOffscreenPixmaps" "true"
#	Option		"AccelMethod"	"EXA"
EndSection

Section "Device"
	Identifier	"Screen0 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"	"on"
	Option		"backingstore"	"on"
    Option "AllowGLXWithComposite" "true"
	Screen		0
	Option          "XAANoOffscreenPixmaps" "true"
#	Option		"AccelMethod"	"EXA"
EndSection

Section "Device"
	Identifier	"Screen1 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"	"on"
	Option		"backingstore"	"on"
    Option "AllowGLXWithComposite" "true"
	Screen		1
	Option          "XAANoOffscreenPixmaps" "true"
#	Option		"AccelMethod"	"EXA"
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
    VendorName "Plug'n Play"
    ModelName "F-417"
    HorizSync 24-80
    VertRefresh 49-75
    
    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
    VendorName "Plug'n Play"
    ModelName "F-417"
    HorizSync 24-80
    VertRefresh 49-75
    
    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"MergedFB Screen"
	Device		"MergedFB ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"MergedFB2 Screen"
	Device		"MergedFB2 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Screen0 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Screen1 ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DefaultLayout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerLayout"
	Identifier	"MergedFBLayout"
	Screen		"MergedFB Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerLayout"
	Identifier	"MergedFB2Layout"
	Screen		"MergedFB2 Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerLayout"
	Identifier	"XineramaLayout"
	Screen		"Screen0"
	Screen		"Screen1" LeftOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"TwoHeadLayout"
	Screen		"Screen0"
	Screen		"Screen1" LeftOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
  	Option		"DefaultServerLayout"	"MergedFB2Layout"
# If enabled, lets you deactivate KB/Mouse grabs with Ctrl+Alt+KP_Divide
#	Option		"AllowDeactivateGrabs"	"on"
# If enabled, lets you kill clients that grab the server with Ctrl+Alt+KP_Multiply
#	Option		"AllowClosedownGrabs"	"on"
EndSection

Section "Extensions"
    Option "backingstore" "true"
    Option "Composite"    "Enable"
    Option "RENDER"       "Enable"
EndSection

```

With the help of [http://ubuntuforums.org/showthread.php?t=301951](http://ubuntuforums.org/showthread.php?t=301951) I wrote a new xorg.conf, but with this one, only one of my two monitors shows an image, the other one is in standby mode (so it doesn't even get a signal, in contrast to the above configuration file, where both monitors show the same). Furthermore, if I switch to the console or kill the xserver, it shows not the console, but a black screen with this configuration. The above configuration file doesn't have this problem.

```
Section "Module"
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbModel"	"ltcd"
	Option		"XkbLayout"	"de"
    Option "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"	"on"
	Option		"backingstore"	"on"
    Option "AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
    VendorName "Plug'n Play"
    ModelName "F-417"
    HorizSync 24-80
    VertRefresh 49-75
    
    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
    VendorName "Plug'n Play"
    ModelName "F-417"
    HorizSync 24-80
    VertRefresh 49-75
    
    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DefaultLayout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
# If enabled, lets you deactivate KB/Mouse grabs with Ctrl+Alt+KP_Divide
#	Option		"AllowDeactivateGrabs"	"on"
# If enabled, lets you kill clients that grab the server with Ctrl+Alt+KP_Multiply
#	Option		"AllowClosedownGrabs"	"on"
EndSection

Section "Extensions"
    Option "backingstore" "true"
    Option "Composite" "Enable"
    Option "RENDER" "Enable"
EndSection

```

I want to have one "big screen", splitted over both monitors. Any advice why the old configuration file doesn't work anymore and how to solve my problem?

Thanks!
Julian

---

### Post by jvm on 2007-04-22
No idea? Some people here who use Xinerama with Xorg 7.2?

---

### Post by jvm on 2007-04-22
Any advice where I should search for information? Is there some mailinglist where I should ask instead?

---

