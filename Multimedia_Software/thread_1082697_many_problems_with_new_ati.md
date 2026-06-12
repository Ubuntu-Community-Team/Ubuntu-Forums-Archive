---
title: "many problems with new ati"
date: 2009-02-28
forum: Multimedia Software
---

### Post by veganbikepunk on 2009-02-28
I just got a new Radeon X1650 Pro AGP card.  I popped it in and booted it up and was told (as expected) that there were proprietary drives I could be using, so I activated them, but it stayed at 0% for downloading.  So I went to Synaptic and searched fglrx and found I already had the necessary files downloaded.  Then I edited my xorg to activate it and restarted x.  It restarted all right but I couldn't turn on my desktop effects.  So i googled around and found some ways to edit the xorg that it claimed would work.  I'm sorry, but I don't know what those ways were.  My friend had a similar setup so I backed mine up and used his.  Now it goes to like 400x300 resolution when I start X, and I have to go into catalyst and change it, and on top of that, I still can't use desktop effects.  GAH!  Your help is much appreciated.  I'm using intrepid ibix, and gnome.

My old Xorg, backed up (xorg.conf.old)

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
	Option "AIGLX" "True"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```

my friend's (and my new) xorg.conf
```
Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1400x1050" "1400x1050" "1280x1024" "1280x1024" "1280x960" "1280x960" "1024x768" "1024x768" "800x600" "800x600" "640x480" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105+inet"
	Option	    "XkbLayout" "us"
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Option	    "OpenGLOverlay" "off"
	Option	    "VideoOverlay" "on"
	Driver	"fglrx"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection

```

---

