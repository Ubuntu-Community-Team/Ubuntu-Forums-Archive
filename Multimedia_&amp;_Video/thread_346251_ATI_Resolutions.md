---
title: "ATI Resolutions"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by marcantonio on 2007-01-25
I have an HP nw8440 with a ATI FireGL v5200 in it.  I installed the latest drivers from ATI (8.33.6) and it seems fine, except, for the resolution.  It has a widescreen and the only 16:10 resolution that seems to be supported is 1920x1200.  I would really like to get it down to 1680x1050 or 1440x900.  From Xorg.log.0:

```
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 151.8 MHz   Image Size:  332 x 208 mm
(II) fglrx(0): h_active: 1920  h_sync: 2020  h_sync_end 2052 h_blank_end 2184 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1202  v_sync_end 1208 v_blanking: 1235 v_border: 0
(II) fglrx(0):  TMDISPLAY
(II) fglrx(0):  LTD154EZ0C
(II) fglrx(0): End of Display1 EDID data --------------------

<snip>

(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1200 (pitch 0)
(**) fglrx(0): *Mode "1920x1200": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"  151.75  1920 2020 2052 2184  1200 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1920x1080": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  151.75  1920 2020 2052 2184  1080 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1600x1200": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  151.75  1600 2020 2052 2184  1200 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1280x1024": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  151.75  1280 2020 2052 2184  1024 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  151.75  1152 2020 2052 2184  864 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  151.75  1024 2020 2052 2184  768 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  151.75  800 2020 2052 2184  600 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  151.75  640 2020 2052 2184  480 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  151.75  640 2020 2052 2184  400 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  151.75  512 2020 2052 2184  384 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  151.75  400 2020 2052 2184  300 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  151.75  320 2020 2052 2184  240 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  151.75  320 2020 2052 2184  200 1206 1208 1235 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (147, 145)
(--) fglrx(0): Virtual size is 1920x1200 (pitch 1920)
(**) fglrx(0): *Mode "1920x1200": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"  151.75  1920 2020 2052 2184  1200 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1920x1080": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  151.75  1920 2020 2052 2184  1080 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1600x1200": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  151.75  1600 2020 2052 2184  1200 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1280x1024": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  151.75  1280 2020 2052 2184  1024 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  151.75  1152 2020 2052 2184  864 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  151.75  1024 2020 2052 2184  768 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  151.75  800 2020 2052 2184  600 1206 1208 1235 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  151.75  640 2020 2052 2184  480 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  151.75  640 2020 2052 2184  400 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  151.75  512 2020 2052 2184  384 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  151.75  400 2020 2052 2184  300 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  151.75  320 2020 2052 2184  240 1206 1208 1235 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 151.8 MHz (scaled from 0.0 MHz), 69.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  151.75  320 2020 2052 2184  200 1206 1208 1235 +hsync +vsync
```

If anyone has any ideas I'd appreciate it.

Thanks,
Marc

---

### Post by MiniMe on 2007-02-15
I managed to get my 22" LCD widescreen going at 1680x1050 and 1440x900 with my ATI radeon X800 pro. From what I remember the steps were:

1. I installed the ati drivers as per the instructions here [http://davidwinter.me.uk/articles/2006/10/25/getting-ubuntu-dapper-to-dance-with-ati-x800-gto/](http://davidwinter.me.uk/articles/2006/10/25/getting-ubuntu-dapper-to-dance-with-ati-x800-gto/)

2. Edited the xorg.conf file (in /etc/X11) by adding the following to the ' Section "Monitor" ' area:

To use 1680x1050 I added the following line:
	ModeLine 	"1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync

To use 1440x900 I added these two lines:
	Modeline	"1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
	Modeline 	"1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync

Then I selected the desired resolution in System -> Preferences -> Screen Resolution

For some reason, the option to use both resolutions wasn't there, when I added all of the above lines, I couldn't choose 1680x1050, it was only when I commented out the 1440x900 lines that I could use 1680x1050. But then I couldn't choose 1440x900. It would be nice if I could get both to show up in the Screen Resolution preferences but it's not the end of the world because I rarely need to change resolutions. Also, using 1440x900 at 70Hz resulted in blurry text, so I set it to 60Hz and all is fine.

Don't ask me what all those numbers beside the resolution are because I have no idea, but if you do have a clue, I'd love to hear about it.

Here's are some sections of my xorg.conf file that might help also. Good luck! To me it's mostly gibberish but it works for me, so here you go:

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	ModeLine 	"1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync
#uncomment next two lines and delete above line to enable 1440x900
#	Modeline	"1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
#	Modeline 	"1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R423 UI [Radeon X800PRO (PCIE)]"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Centermode" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R423 UI [Radeon X800PRO (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	Option	    "UseEdidFreqs" "false"
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
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
		Modes		"1440x900_70.00" "1440x900_60.00"
	EndSubSection
EndSection

---

### Post by Dave82 on 2007-02-23
My laptop is a Thinkpad Z61p and it has an ATI FireGL V5200 too. I have the same problem as marcantonio. The only resolutions available are: 1920x1200, 1920x1080, 1600x1200, 1280x1024, 1152x864, 1024x768, 960x600, 800x600, 640x480.
I think I installed fglrx correctly because my fglrxinfo output is:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.6011 (8.28.8)
```
However, no matter what I specify through aticonfig --resolution, the available resolutions in System > Preferences > Screen Resolution don't change (I'd like to set it to 1680x1050 too).
I tried adding the ModeLine thing as MiniMe suggested, but it didn't work.
This is part of my xorg.conf after aticonfig --resolution:
```
Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
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
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```
I also tried to cleanup the file deleting:
```
Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        .......................................
EndSection
```
Last experiment was this:
```
Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
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
                Modes    "1920x1200" "1680x1050" "1440x900" "1280x800"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```
None of these worked. And yes, I remembered to restart Xorg or reboot every time.
Please help me! Am I missing something?
Thanks

---

### Post by MiniMe on 2007-02-24
Not sure why it's not working for you marcantonio. I managed to get both resolutions 1680x1050" "1440x900" available in System -> Preferences -> Screen resolution by making having them both in the modeline. Below is my current xorg.conf file in its entirety. It seems like you've already played around quite a bit so this might not help, but you never know. Good luck! 

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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "false"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
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
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	ModeLine 	"1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync
#next line is for 70Hz, doesn't work well for my LCD screen
#	Modeline	"1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
	Modeline 	"1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R423 UI [Radeon X800PRO (PCIE)]"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Centermode" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R423 UI [Radeon X800PRO (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	Option	    "UseEdidFreqs" "false"
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1440x900" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
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
# next line lets me have both resolutions available in System -> Preferences -> Screen resolution
		Modes		"1680x1050" "1440x900_60.00" 
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by marcantonio on 2007-02-26
From what I've read on [this forum]("http://rage3d.com/board/forumdisplay.php?f=88") the newer drivers ignore custom modelines.  MiniMe what version of the driver are you using?

---

### Post by MiniMe on 2007-03-06
To be honest, I don't know what version of the ATI drivers I'm using. Being a newbie, I'm not sure how to check either. I installed them about a  month ago using these commands:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

If you let me know how I can check the driver version, I'll be happy to get back to you with the info.

For me the modeline was indeed required in order to get the resolution options available in System > Preferences > Screen Resolution


Cheers.

---

### Post by marcantonio on 2007-03-07
```
$ fglrxinfo
```

---

### Post by MiniMe on 2007-03-08
Here's what was returned when I typed in fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.5814 (8.25.18)

Hope it helps.

---

