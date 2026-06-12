---
title: "Ubuntu 7.10 and ATI X300 Dual head video card"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by kristoffer.a on 2007-11-01
I just installed 7.10 at my office workstation where I have a ATI X300 video card with two Dell 1907FP monitors connected via DVI. It has always worked flawless with a certain other OS from Redmond.
Now I have spent a good full working day reading forum threads, blogs posts and what not to get this setup to work from within Ubuntu but has failed.

I do not run the proprietary ATI driver since it seems I can't get both dual head with XrandR and those cool desktop effects using it (read it somewhere). So I have resorted to the default ATI driver for my card but still no luck.

xrandr detects possible outputs on both DVI-0 and DVI-1 and when looking at the xorg log file it looks like the X server also detects the screens by model name and video modes on both DVI-0 and DVI-1 outputs.

My result so far:

The login screen is neatly displayed on both screens (with the actual login window on the left screen and an extension of the background, to which I can move the mouse pointer on the right screen). 

When I have logged in the right screen shuts down and can't be used. The displayconfig-gtk tool will not detect both screens (however it shows two versions of Screen 1).

Has anyone managed to get this (or a similar) setup to work? I'm getting desperate here, with all my co-workers saying "Haha, you should stick to Windows", et.c. I'm certainly not gonna give them the joy of seeing me fail with a simple task like this. So I'd be happy for any advice or solution.

Below is the output of XrandR from within my current X session, as well as a copy of my xorg.conf.

```

kran@zys-kran:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
DVI-1 connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0 +   75.0*    59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-0 connected (normal left inverted right)
   1280x1024      60.0 +   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  


```

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

Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "monitor-DVI-1" "DELL 1907FP"
	Option "monitor-DVI-0" "DELL 1907FP-2"
EndSection

Section "Monitor"
	Identifier	"DELL 1907FP"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"DELL 1907FP-2"
	Option		"DPMS"
	Option		"RightOf" "DELL 1907FP"
	Option		"Enable" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"DELL 1907FP"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Virtual 2560 1024		
		Modes "1280x1024@75" "1280x1024@60"
		#Modes "1280x1024@75" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Light- on 2007-11-02
It is possible to have desktop effects with the proprietry ATI driver. You need to install xserver-xgl though.

You will not be able to get desktop effects to work if your monitors exceed the MAX_TEXTURE_SIZE of your video card. Im not sure what yours is, but mine is 2048x2048 which means that I would have to run my lovely 22" LCD at 1024x768 to get desktop effects.

Anyway, your xorg.conf doesnt accomodate a second monitor. Since you are using the opensource drivers, I would suggest Xinerama mode. To do that, you need to make a copies of your device, monitor and screen sections (you currently only have a copy of your monitor section).

> 
Section "Device"
	Identifier	"0 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Screen 0
EndSection

#added device section, and changed it a little
Section "Device"
	Identifier	"1 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Screen 1
EndSection

#i modified your monitor section a little
Section "Monitor"
	Identifier	"0 DELL 1907FP"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"1 DELL 1907FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"0 Default Screen"
	Device		"0 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"0 DELL 1907FP"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1280x1024@60"
	EndSubSection
EndSection

#added other screen
Section "Screen"
	Identifier	"1 Default Screen"
	Device		"1 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"1 DELL 1907FP"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1280x1024@60" 
	EndSubSection
EndSection

Section "ServerLayout"
        Option "Xinerama" "true"
	Identifier	"Default Layout"
	Screen		0 "0 Default Screen" 0 0
        Screen          1 "1 Default Screen" RightOf "0 Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


---

### Post by daniel.martinez on 2007-11-28
I have the same problem with my ATI. I tried that configuration, but my dual-head doesn't work. When I restart the xorg, the system comes mad and lose all the configuration, showing me the displayconfig-gtk to configure it again, and the second screen always be disable to change.

The only possible difference with the main post is that xrandr give me a VGA-0 and a DVI-0:
> Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1400 x 1200
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9  
   1400x1050@60   60.0  
   1280x1024@60   60.0  
   1280x960@60    60.0  
   1280x960       59.9  
   1152x864@75    75.0  
   1152x864       75.0     74.8  
   1024x768@85    85.0  
   1024x768@75    75.1  
   1024x768       75.1     70.1     60.0  
   1024x768@70    70.1  
   1024x768@60    60.0  
   1024x768@43    43.5  
   832x624@75     74.6  
   832x624        74.6  
   800x600@85     85.1  
   800x600@72     72.2  
   800x600        72.2     75.0     60.3     56.2  
   800x600@75     75.0  
   800x600@60     60.3  
   800x600@56     56.2  
   640x480@85     85.0  
   640x480@72     72.8  
   640x480@75     75.0  
   640x480        75.0     72.8     66.7     60.0  
   640x480@60     60.0  
   720x400        70.1  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 306mm x 230mm
   1280x1024      59.9* 
   1280x960       59.9  
   1152x864       74.8  
   1024x768       84.9     75.1     70.1     60.0  
   832x624        74.6  
   800x600        99.7     84.9     72.2     75.0     60.3  
   640x480        99.8     84.6     75.0     72.8     60.0  
   720x400        70.1  
   640x350        70.1  
S-video disconnected (normal left inverted right)

My current (working) configuration is this one (I remove unused modeline with [...]):
> Section "ServerLayout"
  Identifier "X.org Configured"
  Screen 0 "Screen0" 0 0
  InputDevice "Mouse0" "CorePointer"
  InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
  RgbPath "/etc/X11/rgb"
  ModulePath "/usr/lib/xorg/modules"
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/X11R6/lib/X11/fonts/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/X11R6/lib/X11/fonts/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "GLcore"
  Load "dbe"
  Load "dri"
  Load "extmod"
  Load "glx"
  Load "record"
  Load "xtrap"
  Load "vnc"
  Load "type1"
  Load "v4l"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "kbd"
EndSection

Section "InputDevice"
  Identifier "Mouse0"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/input/mice"
  Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
  identifier "Monitor0"
  vendorname "PHL"
  modelname "Philips 170S"
[...]
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
[...]
  gamma 1.0
EndSection

Section "Monitor"
  identifier "Monitor1"
  vendorname "PHL"
  modelname "Philips 107E"
[...]
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
[...]
  gamma 1.0
EndSection

Section "Device"
  identifier "ATI0"
  boardname "ATI Radeon"
  busid "PCI:1:0:0"
  driver "radeon"
  screen 0
  vendorname "ATI"
EndSection

Section "Device"
  identifier "ATI1"
  boardname "ATI Radeon"
  busid "PCI:1:0:0"
  driver "radeon"
  screen 1
  vendorname "ATI"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "ATI0"
  Monitor "Monitor1"
  DefaultDepth 24
  SubSection "Display"
    depth 24
#    virtual 2560 2048
    modes "1280x1024"
  EndSubSection
EndSection

Section "Screen"
  Identifier "Screen1"
  Device "ATI1"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    depth 24
#    virtual 1792 1344
    modes "1280x1024"
  EndSubSection
EndSection

My last try was change the ServerLayout section with this:
> Section "ServerLayout"
  Identifier "X.org Configured"
  Option "Xinerama" "on"
  Screen 0 "Screen0" 0 0
  Screen 1 "Screen1" LeftOf "Screen0"
  InputDevice "Mouse0" "CorePointer"
  InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Something wrong in the xorg.conf?

---

