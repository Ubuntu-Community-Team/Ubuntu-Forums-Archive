---
title: "Problem installing ATI drver"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by TC-cheesy on 2007-11-18
Hello.

I am trying to get my card to work correctly with the new ATI driver (8.42.3)
I have taken many steps to try and fix this. First I'll tell you what I've done. 

When I installed Ubuntu 7.10, I used the -rt kernel, but then learned that fglrx wouldn't be compatible "FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'"

so, I installed the latest generic kernel. I installed the kernel manually according to [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") and I still had this problem
```
dylan@MILLENIA:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

so I completly uninstalled fglrx and reinstalled it according to the guide. and when I rebooted the computer, I got a blank black screen where it should of loaded to my login screen.  I try to run in reco0ver mode, and I get a blank screen after I type "startx"

I realised this is the same problem as when I try to use the opensource "radeon" driver.


here is my xorg.conf as of current ( I commented out device options and loaded with the vesa driver):

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
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
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver	"vesa"
#	Option	"VideoOverlay" "on"
#	Option	"OpenGLOverlay" "off"
#	Option	"DRI" "true"
#	Option	"UseFastTLS" "2"
#	Option	"XaaNoOffscreenPixmaps"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

so is there anyway I could fix this problem? thanks for any help.

EDIT: forgot to mention my video card. it's an ATI Radeon 9600 XT.

---

### Post by Cochise on 2007-11-18
change:
ection "Device"
	Identifier  "aticonfig-Device[0]"
	Driver	"vesa"
#	Option	"VideoOverlay" "on"
#	Option	"OpenGLOverlay" "off"
#	Option	"DRI" "true"
#	Option	"UseFastTLS" "2"
#	Option	"XaaNoOffscreenPixmaps"
EndSection

to:
ection "Device"
	Identifier  "aticonfig-Device[0]"
	Driver	"fglrx"
#	Option	"VideoOverlay" "on"
#	Option	"OpenGLOverlay" "off"
#	Option	"DRI" "true"
#	Option	"UseFastTLS" "2"
#	Option	"XaaNoOffscreenPixmaps"
EndSection

---

### Post by TC-cheesy on 2007-11-18
yes, it was like this, and I recieved a blank screen upon starting up. the computer was in freeze too. nothing was working. no disk activity.

---

