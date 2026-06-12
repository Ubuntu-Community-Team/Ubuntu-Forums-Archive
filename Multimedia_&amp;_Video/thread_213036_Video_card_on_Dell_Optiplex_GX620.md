---
title: "Video card on Dell Optiplex GX620"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by fnando on 2006-07-10
Hi.

I received a new computer today, on my work.
I installed Ubuntu Dapper but screen resolution goes only up to 1024x768 in 60mhz.

I have a 19" monitor and I want to use it in 1400x900 or at least 1280x1024.

Is there any way to force resolution or properly configure this computer?

[UPDATE] I found some specs about this computer[1]. The video card is ATI Radeon X600

[1] [http://www.dell.com/content/products/productdetails.aspx/optix_gx620?c=us&l=en&s=bsd&cs=04](http://www.dell.com/content/products/productdetails.aspx/optix_gx620?c=us&l=en&s=bsd&cs=04)

---

### Post by philgomes on 2006-07-17
I'm actually interested in finding 1400x900 support as well. I know my graphics setup supports it. Any ideas?

---

### Post by RyanGT on 2006-08-02
I have a Dell Optiplex GX620 as well with the ATI Radeon x600 card.  Both the Dapper live CD and the default install fail to find a monitor.  Did you have to do something tricky to get the monitor to work at all with X?

Thanks,

Ryan

---

### Post by princemanjee on 2007-06-27
I have the GX 620 and I am having trouble getting my Dual head ATI x600 card to do multi screen AND 3D at the same time... even if I lower the resolution so that it meets the *x2048 limitation. I am running ubuntu 7...

Here is my Xorg.conf File for working Multi display (Wide desktop) However NO working 3D and I HAVE tried chanigng DRI and Composite settings... I have also tried creating a different session for starting X... would like ot get Compiz or Beryl working to increase desktop space...

```


#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
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
	HorizSync    28.0 - 57.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver      "ati"
	Option	    "MonitorLayout" "LCD, CRT"
	Option	    "CRT2Position" "RightOf"
	Option	    "MetaModes" "1024x768-1024x768"
#	Option	    "MergedXinerama" "on"
	Option	    "MergedNonRectangular" "true"
	Option	    "MergedFB" "true"
	BusID       "PCI:1:0:0"
Option "RenderAccel" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
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
	Option	    "Composite"
EndSection

```

Any Help?

---

### Post by servo153 on 2007-07-05
For getting widescreen resolutions to work, try installing the 915resolution package.  I had to install it on a latitude D620 in order for the widescreen resolution to work.

---

### Post by princemanjee on 2007-07-14
I have the Wide screen working fine the problem I am having is getting the Wide screen AND 3D to work simultaneously... Any help? (look at previous post for config details.

---

