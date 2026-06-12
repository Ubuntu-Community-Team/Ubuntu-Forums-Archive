---
title: "direct rendering: yes, but no video"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by bsunde on 2007-07-19
Hi,

I really want to upgrade to Feisty (I have Dapper) but my ATI Radeon 9100 (R200) is not being cooperative.  Using the Live CD, I have this issue:  I apparently get direct rendering but the video screen is blank when I try to play any video files.  Come to think of it, I had the same problem in Dapper, and the issue was fixed only when i got the fglrx driver.  However, this solution doesn't seem to work in Feisty as the new fglrx driver doesnt support my old card and the old driver wont work with the new kernel.  The documentation on the web says that the open source ati driver is supposed to work for my card....but unless I can figure this out I guess I will be looking for a new card.  Any help appreciated.

---

### Post by Crazyhun on 2007-07-19
I have the same problem using Fiesty.  I get sound when playing DivX or DVD's, but no video.

I have a Toshiba Tecra M1, that has a Trident Cyberblade vid card in it.

---

### Post by bsunde on 2007-07-25
OK.  I'd REALLY  like to get this to work, so I thought that posting more information might help.  

I am currently using Dapper.  For a while I was using the propietary ati driver (fglrx) which I finally got to work OK.  But since I want to upgrade to Fiesty I will have to fall back on the open source "ati" driver.  I followed the instructions at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) carefully.  Some things seem to work and some do not.  

[COLOR="Red"]What will work:  direct rendering, glxgears, and flash videos.[/COLOR]

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

[COLOR="Red"]What will NOT work: all other video files (including .ogg) using gxine, mplayer.  I get sound, but no picture.[/COLOR]

Below I have posted my card info and xorg.conf.  Thanks!


~$ lspci

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QM [Radeon 9100]



# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "ServerLayout"
	Identifier     "Default Layout"
	Option          "AIGLX"         "true"
	Screen         "Default Screen" 0 0
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
	Identifier   "LCD-MONITOR"
	HorizSync    30.0 - 65.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R200 QM [Radeon 9100]"
	Driver      "ati"
	#Option	    "VideoOverlay" "on"
	#Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
        Option      "XAANoOffscreenPixmaps"
        Option "BusType" "PCI"
        Option "UseFBDev" "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R200 QM [Radeon 9100]"
	Monitor    "LCD-MONITOR"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by furyy on 2007-08-03
My R1950 pro went back to the shoppe so im sitting on my radeon 9200 again and what i found out is that Gstreamer default video output is through the Ati Video Overlay sink. This translates into the overlay being behind the player's window ( covered by it) so i have to wobble the window a bit and overlay pops back on top (and no wobbly effect etc) :S Might set the sink to use no xv through gstreamer-properties but then video playback gets SLOW (and sdl doesn't work??) :S

---

### Post by tseliot on 2007-08-03
Maybe you should try installing the codecs:
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

and install totem-xine or kaffeine-xine, mplayer or vlc

---

### Post by bsunde on 2007-08-14
Sorry...I should have been more clear.  I installed the codecs months ago and my video worked great for a long time.  The problem is that the newer ait drivers do not work on the video card and the older driver I had used  is not in Feisty.  Oh well...I gave up and got a newer card.  Worked great without a hitch.

---

