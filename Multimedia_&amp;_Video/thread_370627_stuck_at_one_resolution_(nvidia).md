---
title: "stuck at one resolution (nvidia)"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by frenchtomytoast on 2007-02-25
I'm stuck at max resolution at 1920x1200, I would like to change to 1400x1050 but I'm not given the option to when i go to System -> Preferences -> Screen Resolution

I've tried editing xorg.conf and that didn't work, and I tried reconfiguring via terminal. Neither works. Here is my xorg.conf:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by tgalati4 on 2007-02-26
You said that you edited xorg.conf, but I see all of the higher resolutions in the file that you posted.  Did you remove all of the unwanted (higher) resolutions from xorg.conf and then do a control-alt-backspace to restart X.

Good luck.

---

### Post by RudolfMDLT on 2007-02-26
X will default to the highest res - this is an annoying fact! Here is how I get the res I want!

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"[COLOR="Red"]1280x1024[/COLOR]" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"[COLOR="Red"]1280x1024[/COLOR]" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"[COLOR="Red"]1280x1024[/COLOR]" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection




No other options in front of the res that you want.

Goodluck,

Cheers!

---

### Post by frenchtomytoast on 2007-02-26
I removed all the higher resolutions and still it operates at 1900x1200.

Also, when I kill X to operate at command line only, I get a blank screen. Any thoughts?

---

### Post by RudolfMDLT on 2007-02-26
could you post the content of your xorg.conf file? ht entire thing, but post it in php tags! secondly use the Nvidia configuration utility to config your res and not gnome or KDE's applet. 

I run KDE and not gnome so open up the terminal and run it like this: sudo nvidia-settings


Goodluck,

Cheers,

Rudolf

---

### Post by frenchtomytoast on 2007-02-26
Here is the entire contents of my xorg.conf.

[PHP]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/PHP]

---

### Post by RudolfMDLT on 2007-02-26
:confused: 

sudo dpkg-reconfigure -phigh xserver-xorg

I the only thing that I can think of - or as a last resort:

sudo su
apt-get remove nvidia-glx

restart you computer

sudo apt-get install nvidia-glx

---

### Post by Pikestaff on 2007-02-26
Try reconfiguring xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose all the defaults as you go through (or any customizations you may want/need) until you get to a part where it asks you what resolutions you would like to use on your computer.  Arrow down and find the resolution you want and press spacebar to select it and then press enter to continue.  Then reboot after you finish.  Try that...

---

### Post by adamthompson on 2007-02-26
Do you have something like Main Menu -> System Tools -> NVIDIA X Server Settings or Main Menu -> System Tools -> NVIDIA Settings? If you do, try to use that instead of System -> Preferences -> Screen Resolution. If it works, restart your computer and see if it keeps your preferred resolution.

---

### Post by RudolfMDLT on 2007-02-26
both:

sudo dpkg-reconfigure xserver-xorg

and

Main Menu -> System Tools -> NVIDIA X Server Settings or Main Menu -> System Tools -> NVIDIA Settings

are graphical manipulators of the Xorg file. X just ain't listening to the file? weird? That why I suggested re-installing the driver but I don't have too much faith in that...

---

### Post by Pikestaff on 2007-02-26
> **RudolfMDLT said:**
> both:

sudo dpkg-reconfigure xserver-xorg

and

Main Menu -> System Tools -> NVIDIA X Server Settings or Main Menu -> System Tools -> NVIDIA Settings

are graphical manipulators of the Xorg file. X just ain't listening to the file? weird? That why I suggested re-installing the driver but I don't have too much faith in that...

Well, see, I had a very similar problem and when I edited the file it didn't change anything, but dpkg-reconfigure xserver-xorg did.  I'm not sure why, but yeah :P

---

### Post by RudolfMDLT on 2007-02-27
neither am I...:lol:

---

### Post by frenchtomytoast on 2007-02-27
Thanks for all your help thus far.
Tried everything suggested, and no solution has worked yet.
Still working on it, and I'll post back if I come up with something.

---

### Post by tgalati4 on 2007-02-27
I assume that other resolutions work OK under Windows?  Is it a subtle hardware problem?  Perhaps there is an interrupt or I/O address that is misdirected, so the card just assumes the highest resolution.

In the BIOS, try turning off the parallel port, serial ports, USB port, power management, and Plug N Play Operating System.  Then see if your video card behaves.

---

### Post by frenchtomytoast on 2007-02-27
All the resolutions work in Windows XP. 
It's possible because I have 2 graphics cards that operate on a switch (allowing only one to be used at a time) that there are some funky things in the bios.

---

### Post by tgalati4 on 2007-02-28
Linux hates ambiguity.  Is this a hot-key switch, that you can switch between video cards?  Did you try pulling one of the video cards, or designating the nVidia card as the primary boot video card?

Could be a hardware detection limitation in the kernel.  Perhaps you should post it at kernel.org.  I don't know how Linux handles a video card that can be switched off.  You can tell the xserver about multiple displays and then turn them on and off.  But switching the actual hardware is another matter.

Good luck.

---

### Post by frenchtomytoast on 2007-02-28
It's an Alienware laptop running an agp geforce card and an onboard intel video chip.
There is a switch on the outside of the laptop that can be switched when the power is off and I'm assuming the bios detects which card is running by that switch on boot. How it works exactly, I haven't figured out. I just run it on the nvidia card and live with it. The onboard is just for battery saving.

---

