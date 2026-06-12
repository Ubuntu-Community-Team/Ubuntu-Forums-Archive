---
title: "Edgy fglrx video playback problem"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by antimoni on 2006-10-28
I upgraded from Dapper to Edgy. I have ATI Radeon 9600 video card and dual monitor system with big desktop. Driver is Edgy's Included Driver.

I have strange problem with video playback. Video is positioned half outside left screen and I have to "pick it up" with player window. Video sticks in player and I can drag it to normal position, but only in the left monitor. Right monitor shows only black video window.

In Dapper I could watch video in both monitors.

Here is my xorg.conf
```
# File: xorg.conf

Section "dri"
	Mode 0666
EndSection

Section "Module"
	Load	"bitmap" 	
	Load	"ddc" 		
	Load	"int10" 	
#	Load	"v4l" 		
	Load	"vbe" 		
    	Load    "dbe"  	
    	SubSection  "extmod"
      		Option    "omit xfree86-dga"   # don't initialise the DGA extension
    	EndSubSection
    	Load        "type1"
    	Load        "freetype"
   	Load        "glx"  
    	Load        "dri"   
EndSection

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS" 
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS" 
EndSection

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"

    Option "DesktopSetup"               "0x00000200" 

    Option "MonitorLayout"              "AUTO, AUTO"

    Option "NoTV"                       "yes"     


#    Option "GammaCorrectionI"           "0x0701c070"
#    Option "GammaCorrectionII"          "0x06419064"

    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
    Option "UseFBDev"			"on"


    BusID "PCI:2:0:0"    # vendor=1002, device=4150
    Screen 0
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "Server Layout"
    Screen "Screen0"
	InputDevice	"Generic Keyboard"
        InputDevice     "Logitech MX1000" "CorePointer"
EndSection

Section "ServerFlags"
	Option "AIGLX" "off"
EndSection

Section "Extensions"
	Option "Composite" "disable"
EndSection

### EOF ###

```

fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

cat /var/log/Xorg.0.log | grep fglrx | grep -i DRI:
```
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): Initialized in-driver Xinerama extension
(II) fglrx(0): [DRI] installation complete

```

Any ideas how to get video playback working properly?

---

### Post by Bruno Abinader on 2006-11-05
Hi,
I´m running Ubuntu Edgy with fglrx driver on my laptop and I´ve got the same problem too, so I´ve managed to have a "temporary fix" using **Mplayer** with "**gl**" for video playback, and it showed too on the 2nd video output. Maybe you can try that too.

---

