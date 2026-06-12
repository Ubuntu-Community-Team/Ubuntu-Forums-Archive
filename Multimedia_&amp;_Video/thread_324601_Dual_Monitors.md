---
title: "Dual Monitors"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by Varth on 2006-12-24
Well, I got a hold of another monitor today, so I put an old extra graphics card (Nvidia GeForce 2 PCI) into my computer and hooked both of the monitors up. Then I wrote my Xorg.conf file and all that, and restarted X. Both the monitors came up fine, and I could move my mouse between them perfectly. But then I noticed a weird problem. Windows wouldn't move all the way to the other monitor! *gasp* For example:

[IMG]http://img141.imageshack.us/img141/6936/diagrameq8.jpg[/IMG]
(No real screenshot because it'll only take a screenshot of my primary monitor)

So, both monitors are generic 17" CRTs running at 1280x1024. The primary monitor is connected through an onboard Intel chipset, and the secondary monitor is connected through a PCI nVidia GeForce 2. Here's a truncated version of my Xorg.conf file:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver  "kbd"
	Option  "CoreKeyboard"
	Option  "XkbRules"	"xorg"
	Option  "XkbModel"	"pc105"
	Option  "XkbLayout"	"us"
	Option  "XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver  "mouse"
	Option  "CorePointer"
	Option  "Device"  "/dev/input/mice"
	Option  "Protocol"  "ExplorerPS/2"
	Option  "ZAxisMapping"  "4 5"
	Option  "Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Onboard"
	Driver  "i810"
	BusID  "PCI:0:2:0"
EndSection

Section "Device"
	Identifier	"nVidia GeForce 2"
	Driver  "nvidia"
	BusID  "PCI:01:10:0"
EndSection

Section "Monitor"
	Identifier	"Main"
	Option  "DPMS"
EndSection

Section "Monitor"
	Identifier	"Secondary"
	Option  "DPMS"
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device  "Onboard"
	Monitor  "Main"
	DefaultDepth	24
	SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device  "nVidia GeForce 2"
	Monitor  "Secondary"
	DefaultDepth	24
	SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Daul Monitor"
	Screen  "Main Screen"
	Screen  "Secondary Screen" RightOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Any help solving this problem would be greatly appreciated. If you need any other information, just ask. Thanks.

---

### Post by Astro96 on 2006-12-24
Have you considered using NVIDIA's TwinView?  That's working great for me.

---

### Post by Varth on 2006-12-24
I thought TwinView only worked on dual-head nVidia cards. One of my monitors is attached to an onboard Intel, and one is connected to a PCI nVidia GeForce 2.

---

### Post by Cene on 2006-12-24
IIRC the desktops are seperate in Xinerama, so you can't move windows between them.

---

### Post by Varth on 2006-12-24
No. They are two seperate desktops when you DON'T use Xinerama. I had a dual-head setup on this PC with a different monitor once, and it worked fine, desktops and all, and I could move windows between them.

---

### Post by Astro96 on 2006-12-24
Yep, you are right about TwinView.  My mistake.

---

### Post by Varth on 2006-12-26
Bumped.

---

### Post by Varth on 2006-12-26
I fixed it by reinstalling Xinerama

---

