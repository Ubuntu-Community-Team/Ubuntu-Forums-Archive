---
title: "Guild Wars and Wine 0.9.29 CVS"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by Limetang on 2007-01-24
Recently I bought Guild Wars Nightfall and was wanting to play it on Ubuntu (in an attempt to further diminish my use of Windows), so I installed it on Windows, copied the files over to my Ubuntu partition and tried to run it through Wine. It worked pretty well with 8 FPS. I then upgraded to Edgy and have been unable to run it since. I have tried using [this how-to](http://www.ubuntuforums.org/showthread.php?t=283122) to no avail.

When I start Guild Wars, I have a mouse but graphics appear like this:
[img]http://img252.imageshack.us/img252/3345/gw5pg.jpg[/img]

FPS is reported as 1 (although I would approximate it to be more like 0.2), in Dapper I got 8 and in Windows XP I get 50.

When I close the window, Wine returns the following:
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  145 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x0
  Serial number of failed request:  6553
  Current serial number in output stream:  6553
```
As you can tell from this, I am using an ATI video card (ATI Radeon X1300 with 512 MB VRAM - it's not an amazing card, but should be able to play Guild Wars).

fglrxinfo returns the following:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)
```
By the way, I am using bigdesktop with a dual head display (I used "sudo aticonfig --initial --dtop=horizontal --overlay-on=1" to achieve this).

Some information for clarity:
OS: Ubuntu Edgy x86
wine --version: wine-0.9.29-g75c2184
Video card: Sapphire ATI Radeon X1300 with 512 MB VRAM

I suspect this is not a Wine problem but instead a problem with 3D acceleration, so here's xorg.conf:
```
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
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
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
	Option	    "XkbLayout" "gb"
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
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
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
Thanks for any help you might be able to offer, I'm still learning my way around Ubuntu.

---

### Post by waffel on 2007-01-29
Hi LimeTang! ^_^ 
 I have an x800 ATI card wich can play most games at max graphics, but in ubuntu GNU/Linux it could play nothing without it being totally unplayable!

When I tried to play games like Warcraft III and the very first Unreal Turnament wich is even a native GNU/Linux game I had 8 FPS at most!!

The problem is that the bastards of ATI have NOT made some good and usable GNU/Linux drivers where Nvidia have made their drivers maybe even better for GNU/Linux than Windows.

I have just 10 minutes ago changed back to my old Geforce 4 MX 440  wich is not a very good card, but now I can play warcraft III and even Guildwars Factions (although I can't see my mouse yet in GW x_x but I will figure it out ^_^ )

So the best solution is to change to Nvidia even if you're an ATI supporter (wich I almost became), because ATI have NOT made some satisfactory drivers yet unfortunatly!!

Otherwise I wish you a good day and hope this have been of any help!

- - Waffel

---

