---
title: "Solved: ATI 7200 agp and 7000 pci twin monitors"
date: 2006-01-13
forum: Multimedia &amp; Video
---

### Post by replacewindows on 2006-01-13
I just thought I'd post this to help people trying to get two monitors working.

Worked for me:

Need to edit: xorg.conf
I used the Terminal in Applications -> Accessories and typed: cd /etc/X11
then: sudo gedit xorg.conf

Now you can edit xorg.conf. Be careful, you can stop the GUI from loading and also by getting the refresh rates wrong apparently damage older monitors. Best to find out your monitor specs first (horizontal and vertical refresh rates). The only other info needed is the bus ids for your cards. I got this from the terminal by typing: lspci The numbers are in hex so conversion is needed for eg. mine was 0000:00:0b.0 you ignore the first zeros so mine converts to 0:11:0

Now have a look at the xorg.conf below. This will be slightly different for different hardware but basically you only need to add another device, monitor, screen and a couple of lines to the serverlayout.

That's it. I haven't played with my settings yet to see what's possible but to get it working I gave both monitors the same range of refresh rates, and only one mode line each.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

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

Section "Module"
	Load	"GLcore"
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
    Identifier  "radeon0"
    Driver      "ati"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "radeon1"
    Driver      "ati"
    BusID       "PCI:0:11:0"
    Option "BusType" "PCI"
EndSection

Section "Monitor"
    Identifier  "monitor0"
    Option      "DPMS"
    HorizSync 30-65
    VertRefresh 50-75
EndSection

Section "Monitor"
    Identifier  "monitor1"
    Option      "DPMS"
    HorizSync 30-65
    VertRefresh 50-75
EndSection

Section "Screen"
    Identifier  "screen0"
    Device      "radeon0"
    Monitor     "monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier  "screen1"
    Device      "radeon1"
    Monitor     "monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "screen0"
    Screen      "screen1" RightOf "screen0"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    Option "xinerama" "on"
    Option "clone" "off"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

