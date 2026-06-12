---
title: "Modeline Issues with Nvidia 7600GT"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by Feengur on 2007-01-21
Hey guys.  I've tried 4 seperate installations of the NVIDIA-Linux-x86_64-1.0-9746-pkg2 driver package.  I was stuck at 640x480 for the longest time and I eventually got the drivers installed correctly.  Now, i'm having issues with the modelines.  My monitor, refresh rates, and video card are being detected correctly and have been input into the xorg.conf properly it seems, but i'm stuck at 800x600_50 .  ](*,) 

  I recently checked out the X log and here is what it reports:
```
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1440x900"; removing.
(WW) NVIDIA(0): No valid modes for "1400x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1280x960"; removing.
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1280x800"; removing.
(WW) NVIDIA(0): No valid modes for "1280x768"; removing.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(WW) NVIDIA(0): No valid modes for "1152x864"; removing.
(WW) NVIDIA(0): No valid modes for "1152x768"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "640x480"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

No valid modes....  I know these are right. :P  And i know this is where the problem is.  How do I resolve this issue?  Is this with the vid-card?  Or the monitor?  I do notice that it is reporting as:

```
(--) NVIDIA(0):     @@@ (CRT-0)
(--) NVIDIA(0): @@@ (CRT-0): 400.0 MHz maximum pixel clock
```
but in my xorg.conf it is listed properly as "Compaq 7550" .  Here is my xorg.conf for validation.

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
	Identifier	"XFX Nvidia GeForce 7600GT PCIE"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"COMPAQ 7550"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-140
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"XFX Nvidia GeForce 7600GT PCIE"
	Monitor		"COMPAQ 7550"
	Option "UseEdidFreqs" "false"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Any help would be very much appreciated.  I've run through all of the solutions posted about this card on other threads, but none seem to help.  Thanks!

-Feengur

---

### Post by webbca01 on 2007-01-21
Do you have automatix?? If you do, install the nVidia program through that. (Uninstall what you've installed first)(I have the Same Card and I run it in Linux just fine)

If you don't have automatix... follow these instructions: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Best of luck :guitar:

---

### Post by Feengur on 2007-01-22
thanks, i really appreciate the help, The refresh issues have been fixed using automatix, but i still can't change the resolution.  I think maybe the previous drivers didn't uninstall properly though before i ran the automatix install.  How do i revert back to the generic video drivers and still use X so i can operate automatix?  Sorry.  I'm such a noob. :P

---

### Post by majoridiot on 2007-01-22
```
sudo dpkg reconfigure xerver-xorg
```

will reset the config... just restart after the change.

i recommend taking all custom modelines, frequency definitions and the useedidfreqs false and
see what happens.  it looks like the edids are being read correctly, so don't confuse the issue
by redefining them... just let x work it out.  sometimes giving it too much info is contrary.

---

