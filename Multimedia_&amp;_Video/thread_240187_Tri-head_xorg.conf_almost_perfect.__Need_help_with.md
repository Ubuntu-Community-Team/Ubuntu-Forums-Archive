---
title: "Tri-head xorg.conf *almost* perfect.  Need help with virtual console."
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by Joanie on 2006-08-20
Hi all. I just turned my (Edgy) dual-head box into a tri-head one.  And, man, is it cool! 8)  

My xorg.conf seems nearly perfect.  The one problem I'm having is that the display is shot when I try to get into a virtual console (ctrl alt f1). What I find interesting is that this is only the case when I boot normally.  If instead I boot into single-user mode, then immediately log out, X starts up and then I *can* get into the virtual console without difficulty.  What am I missing? ](*,) 

My xorg.config started out as the default, and I added/changed stuff.  In the interest of space, I'm only going to place what I added/changed since I *assume* that the rest is not relevant (?).
```

Section "Monitor"
        Identifier "SyncMaster0"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "SyncMaster1"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "WideScreen"
        Option "DPMS"
EndSection

Section "Device"
        Identifier      "ati0"
        Driver          "ati"
        BusID           "PCI:2:7:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "ati1"
        Driver          "ati"
        BusID           "PCI:2:7:0"
        Screen          1
EndSection

Section "Device"
       Identifier      "ati2"
       Driver          "ati"
       BusID           "PCI:1:0:0"
       Screen           0
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "ati0"
        Monitor         "SyncMaster0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "ati1"
        Monitor         "SyncMaster1"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen2"
        Device          "ati2"
        Monitor         "WideScreen"
        DefaultDepth    24
	SubSection "Display"
		Depth	1
		Modes	"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes	"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes	"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes	"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes	"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes	"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Multihead"
        Screen  "screen2"
        Screen  "screen0" LeftOf "screen2"
	Screen  "screen1" RightOf "screen2"
        InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"	
        Option "Xinerama"
EndSection
```
If anyone has any clues, I'd be most grateful!

---

