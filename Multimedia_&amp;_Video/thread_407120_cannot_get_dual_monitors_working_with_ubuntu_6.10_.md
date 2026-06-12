---
title: "cannot get dual monitors working with ubuntu 6.10 &amp; thinkpad r60"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by fadetoblack82 on 2007-04-11
i've been messing around with xorg.conf for ages now and cannot get a dual screen setup working. i have an external dell monitor in addition to the r60 screen. the problem is that it actually works in the login screen, but when i start a gnome/kde session it goes back to clone mode. any ideas ? here's my xorg.conf

```


Section "ServerLayout"
	Identifier     "Multihead Layout"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen1"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
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
	Option	    "EmulateWheel" "true"
	Option	    "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection


Section "Monitor"
	Identifier   "Monitor0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	HorizSync    31.0 - 64.0
	VertRefresh  58.0 - 60.0
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ati0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "DesktopSetup" "horizontal,reverse" #Enable Big Desktop
    Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Device"
	Identifier  "ati1"
	Driver      "fglrx"
	BusID       "PCI:1:0:1"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "ati0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes "1400x1050" "1280x480" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "ati1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes "1280x1024" "1400x1050" "1280x480" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

Section "ServerFlags"
    Option "AIGLX" "off"
EndSection


```

---

### Post by 00arthuryu on 2007-04-12
when you log in, go to system - preferences - Screen resolution
then change it to the 'top' one (the one which is double your width at the present)

---

### Post by fadetoblack82 on 2007-04-12
that did it, thanks!! i cant believe i spent so much time messing with conf files when all i had to do was change the resolution..

---

### Post by fadetoblack82 on 2007-04-12
ok i have another problem.. for some reason im getting the same resolution on both screens. the laptop screen goes up to 1400x1050 and external monitor goes up to 1920x1200, but the external is displaying at 1400x1050 only. my xorg.conf is the same as in my first post except i changed the Screen1 settings to be:

```

Section "Screen"
    Identifier "Screen1"
    Device     "ati1"
    Monitor    "Monitor1"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
        Modes "1920x1200" "1400x1050" "1280x480" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by mc_plectrum on 2007-04-15
I have exactly the same resolution problem. Have you already found a solution? system - preferences - Screen resolution shows annother resolution as  in the xorg.conf. Both Screens have 1280x800 resolution, but in my xorg.conf is only a resolution of 1280x1024. I want my laptopscreen with 1280x800 and the external Screen with 1280x1024. How do I solve this problem?

[http://www.ubuntuusers.de/paste/9215/?format=txt]("http://www.ubuntuusers.de/paste/9215/?format=txt")

---

### Post by fadetoblack82 on 2007-04-16
unfortunately i haven't figured it out yet - i will let you know if i do. or let me know if you get it working.

---

