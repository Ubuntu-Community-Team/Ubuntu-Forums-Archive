---
title: "Overlay on second screen for TvTime with edgy"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by eagle101 on 2006-12-06
Hi, I had TvTime working on a dual monitor setup with 6.06 LTS.

I have a radeon 9600XT.  I should have saved my xord.conf from Dapper!  But I didn't think it would be a problem!

Now I can't get TvTime to work on the second monitor.  It will work on the primary monitor OK, but dragging the window to the second monitor shows black.

(Say I drag half the window right to the secondary monitor, the video on the secondary monitor is black.) When I drag it the other way, the part that was on the second monitor is still black until I drag it off the left side of the primary screen, then the video will "push back right" in the window.

I've tried:
[http://ubuntuforums.org/showthread.php?t=283791](http://ubuntuforums.org/showthread.php?t=283791)
and implemented a thread involving xinerama.  Now the mouse cursor is a big white box, and I still have no video.

Could someone show me a thread here?  I have been to:
[http://ubuntuforums.org/showthread.php?t=283791](http://ubuntuforums.org/showthread.php?t=283791)
[http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/](http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/)
[http://www.ubuntuforums.org/showthread.php?t=301951&highlight=xinerama](http://www.ubuntuforums.org/showthread.php?t=301951&highlight=xinerama)

Anyway, here is my xorg.conf.  I believe my whole problem is fglrx???  

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0       "Main Screen"
	Screen 1       "Second Screen" RightOf "Main Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option 	       "Xinerama" "true"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
	SubSection  "extmod"
      		Option    "omit xfree86-dga"   # don't initialise the DGA extension
    	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Main Monitor"
	HorizSync    28.0 - 204.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Second Monitor"
	HorizSync    28.0 - 204.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "0 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
	Option 	    "VideoOverlay" "on"
	Option 	    "OpenGLOverlay" "off"
	Screen	    0
	Option 	    "DDCMode" "True"
	Option 	    "MonitorLayout" "primary monitor, secondary monitor"
EndSection

Section "Device"
	Identifier  "1 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
	Option 	    "VideoOverlay" "on"
	Option 	    "OpenGLOverlay" "off"
	Screen 	    1
	Option 	    "DDCMode" "True"
	Option 	    "MonitorLayout" "primary monitor, secondary monitor"
EndSection

Section "Screen"
	Identifier "Second Screen"
	Device     "0 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "Main Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Main Screen"
	Device     "1 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "Second Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

---

### Post by eagle101 on 2006-12-06
A couple hours later, I sort of have it working now...With this configuration I have two separate desktops (I can't drag windows between them)](*,) 
But I can watch TV on the second monitor full screen or in a window.

I tried  sudo aticonfig  --initial=dual-head --dtop=horizontal, but it doesn't seem to have any effect.

Anyway, is the fglrx driver in Edgy a cause of a lot of problems?  Should I use a different one? (For a Radeon 9600XT)

```

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0       "Main Screen"
	Screen 1       "Second Screen" RightOf "Main Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
#	Option 	       "Xinerama" "true"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
#	SubSection  "extmod"
#      		Option    "omit xfree86-dga"   # don't initialise the DGA extension
#    	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Main Monitor"
	HorizSync    28.0 - 204.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Second Monitor"
	HorizSync    28.0 - 204.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "0 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
	Option 	    "VideoOverlay" "on"
	Option 	    "OpenGLOverlay" "off"
	Screen	    0
	Option 	    "DDCMode" "True"
	Option 	    "MonitorLayout" "primary monitor, secondary monitor"
EndSection

Section "Device"
	Identifier  "1 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
	Option 	    "VideoOverlay" "on"
	Option 	    "OpenGLOverlay" "off"
	Screen 	    1
	Option 	    "DDCMode" "True"
	Option 	    "MonitorLayout" "primary monitor, secondary monitor"
EndSection

Section "Screen"
	Identifier "Second Screen"
	Device     "0 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "Main Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Main Screen"
	Device     "1 ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "Second Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "4095x4095" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```

Thanks, Dave

---

### Post by eagle101 on 2006-12-06
Actually, I kind of like two independent desktops :o 

However, if someone could make a suggestion on making one horizontal desktop, with overlay support on both monitors, I'd appreciate that. 

Thanks, Dave

---

