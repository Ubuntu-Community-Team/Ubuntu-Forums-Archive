---
title: "3d acceleration doesn't work after logging off...."
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by murfman on 2007-11-28
OK, this has been driving me nutts for the last few weeks and I am finally looking for some help. I am running 7.1 with dual monitors on a NVIDIA FX-5700, and compiz.  Everything works fine when you first startup until, 3d acceleration and everything.  

But whenh I log out and log back in, I lose 3d acceleration, although compiz seems to be running, but with a different set of preferences.  For example, I normally use desktop plane after I log out and back in it is set to cube and 3d is off...

I have killed gdm and relogged in but it still is not coming back on.  I have to restart to get it to start up.

here's my xorg.conf, let me know if you need more.  

and THANKS!!!!

```

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"
  
  # path to defoma fonts
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "dri"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "stylus"
  Driver "wacom"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Identifier "eraser"
  Driver "wacom"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Identifier "cursor"
  Driver "wacom"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
  identifier "DELL E773c"
  vendorname "Dell"
  modelname "Dell E773c"
  HorizSync 30.0-70.0
  VertRefresh 60-160
  gamma 1.0
  Option "DPMS"
#	SubSection "Display"
#		Depth		24
#		Modes		"1280x1024" "1024x768"
#	EndSubSection
EndSection

Section "monitor" 
  identifier "monitor1"
  vendorname "Dell"
  modelname "Dell E772p"
  HorizSync 30-70
  VertRefresh 60-160
  gamma 1.0
  Option "DPMS"
#	SubSection "Display"
#		Depth		24
#		Modes		"1280x1024" "1024x768"
#	EndSubSection
EndSection

Section "Device"
  identifier "nVidia Corporation NV36.2 [GeForce FX 5700]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
#driver "nv"
  screen 0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "nVidia Corporation NV36.2 [GeForce FX 5700]"
  Monitor "DELL E773c"
  DefaultDepth 24
  option "TwinView"
  option "MetaModes" "1280x1024,1280x1024;1024x768,1024x768"
# option "ConnectedMonitor" "Dell E773c, montior1"
  SubSection "Display"
	Depth	24
	Modes	"1280x1024" "1024x768"
  EndSubSection
EndSection

Section "Extensions"
  option "Composite" "Enable"
EndSection

```

---

### Post by murfman on 2007-11-29
anyone have an idea?  I hate having to restart my bx to get hardware acceleration working.  Can anyone help?

---

### Post by murfman on 2007-11-29
bump

---

