---
title: "Completely removing mesa?"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by toodaloo on 2007-05-14
Is there some way to completely remove mesa drivers without having them affect any other package?
like can you remove the following packages without them uninstalling every other single package?
they've been causing some problems for me on the Radeon 9800, and aiglx doesnt seem to work with them and theres never and direct rendering and glxgears gives around 300 fps which is EXTREMELY low. they also came with the feisty upgrade, so im not sure if they upgraded properly or it just doesnt plain work with my graphics card.

libgl1-mesa-glx
libgl1-mesa-dri
etc.

---

### Post by vtel57 on 2007-05-14
You can just edit your /etc/X11/xorg.conf file to change the mesa driver. If you don't want to use mesa, then you'll probably need to install the proprietary ATI drivers. You'll get MUCH better performance with the proper ATI drivers, anyway.

Luck!

---

### Post by toodaloo on 2007-05-16
Yeah, i already tried doing that, i tired reinstalling my ati drivers, i stried reconfiguring xorg, etc. etc.
none of it works
every fglrxinfo shows that the mesa drivers are the ones that are in use.
my xorg conf shows that im using the fglrx driver, but it actually isnt
in the system>administration>restricted drivers, it says that the proprietary ATI driver is in use
but i still get 300 fps in glxgears, theres no direct rendering still, etc.
edit: more info:
robin@robin-desktop:~$ glxinfo | grep vendor
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

xorg.conf:
omitted comment part

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option		"AIGLX"		"false"
EndSection

Section "Files"

	# path to defoma fonts
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
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
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
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 72.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
	Option		"AIGLX"		"false"
EndSection

Section "Device"
	Identifier  "ATI RADEON 9800"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON 9800"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
.
fglrxinfo:
robin@robin-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

glxgears:
robin@robin-desktop:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1491 frames in 5.2 seconds = 287.218 FPS
1440 frames in 5.2 seconds = 275.121 FPS
1414 frames in 5.3 seconds = 267.772 FPS
1446 frames in 5.2 seconds = 277.063 FPS
1420 frames in 5.1 seconds = 277.470 FPS
1440 frames in 5.1 seconds = 282.424 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 18040 requests (30 known processed) with 0 events remaining.

---

### Post by vtel57 on 2007-05-16
That's mucho screwy. :( I'm not ATI expert. Maybe ATI's website can give you some hints about what's happening with your system? 

Luck!

---

### Post by toodaloo on 2007-05-16
lol, i wish =\
thanks anyways =(.

---

