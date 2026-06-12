---
title: "ATI TV-Out"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by mikeserv on 2007-10-04
I have an ATI X1300 in my machine running on fglrx drivers with a default gnome-xgl session for beryl.  My video card is connected to to a 20" Dell LCD monitor that I prefer to run at 1680*1050 res.  When in Windows I also connect my TV to the SVideo-Out port so that I can watch TV - I tend to download and archive all of the family's shows.

But for some reason I can't figure out how to do this in Ubuntu!  Everytime I try to boot into Ubunutu with the TV connected to the video-card X crashes.  When it does this, it tells me that it can't find any displays for PCI 1:0:1.  My xorg.conf has a device section ascribed to PCI 1:0:0, which is what drives my monitor.  While I'm not not terribly familiar with the concept, I'm starting to get the picture that 1:0:1 is maybe a second head of the video-card and it's what drives a second display?  This confuses me.

I've experimented with all sorts of xorg configurations that I've found posted all over these boards, most of them devoted to some sort of Big Desktop setup, which, though it's not exactly what I want (I'd rather be able to simply switch from monitor to TV like I do in Windows), would be better than no TV display at all.

This xorg.conf setup works as long as I disconnect the TV from the video-card first:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "DELL 2007WFP" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL 2007WFP"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "DELL 2007WFP"
	Device     "Generic Video Card"
	Monitor    "DELL 2007WFP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050_60.00" "1280x1024" "1152x864" "1024x7685" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection


While it's not much of a success some of my experiments have resulted in no display at all.  You may say, "But how can that be a success at all?"  Well, I'm not sure that it is, but I do know that on these occasions at least X did not halt and output an error message.  An example of an xorg.conf that could do that is this:


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         0 "Default Screen"
	Screen         1 "Secondary Screen" LeftOf "Main Screen"	Option	       "Xinerama" "true"  	
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL 2007WFP"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Monitor"
  	Identifier "TV"
  	Option     "DPMS"
  	Gamma      1.0
EndSection

Section "Device"
	Identifier  "ATI RADEON X1300"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
  	Identifier "ATI RADEON X1300.2"
  	BusID "PCI:1:0:1"
                      Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Driver "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON X1300.2"
	Monitor    "DELL 2007WFP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050_60.00" "1280x1024" "1152x864" "1024x7685" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
  Identifier "Secondary Screen"
  Device "ATI RADEON X1300"
  Monitor "TV"
  DefaultDepth 16
  SubSection "Display"
        Depth   16
        Modes   "1024x768"
  EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection



I've been searching everywhere for a solution and experimenting for a week.  I simply can't make it work.  Am I going about this in the wrong way?  As I said before, neither Big Desktop or Xinerama really appeal to me, I simply want to be able to switch displays between my monitor and my tv.

-Mike

---

### Post by mikeserv on 2007-10-05
Bump

---

### Post by randcoop on 2007-10-06
I take a different approach with my Asus F3Jseries laptop, but you might want to give it a try.  The problem with my method is only that I can't simply switch from TV to laptop screen.  Each time I switch, I have to substitute a different xorg.conf file and then re-start KDM (I'm in KDE, but I would think this would work in Gnome by re-starting GDM).

In order to to this, I have two one line scripts (tvon and tvoff).  I have an xorg.conf.tv and and xorg.conf.notv file.  The script tvon just runs sudo cp /etc/X11/xorg.conf.tv /etc/X11/xorg.conf.  Tvoff copies the otherfile to xorg.conf.  Then I re-start KDE (in KDE, that's just CTRL-ALT-BACKSPACE).  

When my monitor is the TV, it's off on my computer.  

Here's the relevant section of my xorg.conf.tv file.  The ForceMonitors line turns on my TV.

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "EnableMonitor" "tv"
	Option	    "TVStandard" "VIDEO"
	Option	    "ForceMonitors" "crtl,tv"
EndSection

In the xorg.conf.notv, the ForceMonitors line turns off the TV and puts it back to the laptop:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "EnableMonitor" "tv"
	Option	    "TVStandard" "VIDEO"
	Option	    "ForceMonitors" "crtl,notv"
EndSection

CAUTION! CAUTION! CAUTION!

I don't know why this works and if you try it, please note that you're doing so at your own risk.  I tried what seemed like a thousand different techniques to get it to work.  I hope this can help, but certainly wouldn't blame you for not trying it.  If you do try it, and it turns off your monitor but doesn't go to the TV, then you'll need to boot into the command line and copy the original xorg.conf file back in order to get back to a GUI screen.  So you should create a backup of a known working xorg.conf before replacing it with anything here.

---

### Post by mikeserv on 2007-10-08
Hell yeah!  That did it.  I have to admit, I didn't think that would work, but now it works for me exactly as you described it!  What I can't understand is why none of the other stuff I tried would work.  But that doesn't matter, this is all I need, and really precisely what I wanted, aside from the logging in thing.  But I think I'm going to create a TV user, anyway.

I don't suppose you could copy that script you use in, could you?

-Mike

---

### Post by randcoop on 2007-10-27
Sorry to be so long in posting a follow up.  I'm happy that the solution worked for you.

In terms of scripts, they're one line copy command:

sudo cp /etc/X11/xorg.conf.tv /etc/X11/xorg.conf

copies the TV on configuration file into xorg.conf.  I call it tvon.  Replace notv for tv in the line to switch back and call it tvoff.  Once I put those lines in two bash files (tvon and tvoff), I just run ./tvon or ./tvoff in the command line.  After running either or, I restart X.

---

