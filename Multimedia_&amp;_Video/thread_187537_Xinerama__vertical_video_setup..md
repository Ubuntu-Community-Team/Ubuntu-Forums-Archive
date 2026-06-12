---
title: "Xinerama / vertical video setup."
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by adam.tropics on 2006-06-03
Ok, so I am using xinerama to extend my laptop display. I have read and experienced problems with different screen resolutions, and with one at 1280x800 (laptop) and one at 1280x1024 (vga) I decided the answer would be to stack, go vertical.

I am able to get that to work, but despite setting the second monitors resolution, it still gives me the same resolution as the laptop, 1280x800. So in Screen resolution dialogue, it runs under 1280x1600. I want to get 1280x1824.

Any ideas?

xorg.conf (such as it is!! )


```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0	"Default Screen"
	Screen 1        "Default Screen" Above "Screen2" 
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

//......Cut for convenience

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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection
//......Cut for convenience

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "KernelModuleParm" "agplock=0"
	Screen	0
	Option	    "DesktopSetup" "vertical"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "ATI2"
	Driver      "fglrx"
	Option	    "KernelModuleParm" "agplock=0"
	Screen	1
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
	Depth     24
	Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "ATI2"
	Monitor    "Monitor2"
	DefaultDepth     24
	SubSection "Display"
	Viewport 0 0
	Depth     24
	Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by Tido on 2006-06-07
[QUOTE=adam.tropics]
Any ideas?

xorg.conf (such as it is!! )


```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0	"Default Screen"
	Screen 1        "Default Screen" Above "Screen2" 
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

```[/QUOTE]

Your whole .conf looks bit wired. I would use good explaining identifiers, makes it also easier to help. a hint: "internal LCD" "external LCD"  

Br,
Tido

---

