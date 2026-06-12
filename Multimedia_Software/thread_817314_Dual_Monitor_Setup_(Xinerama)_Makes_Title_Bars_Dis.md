---
title: "Dual Monitor Setup (Xinerama) Makes Title Bars Disappear..."
date: 2008-06-03
forum: Multimedia Software
---

### Post by MaxMax on 2008-06-03
I'm an Ubuntu beginner (Using 8.04). I modified my xorg.conf to support my two monitors (plugging into one ATI video card). It did extend the desktop over the two monitors, but now there is not title bars appearing on any application windows, making it impossible to move them around. Any suggestions on how to fix that?

Here is the content of the xorg.conf file: 


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	      Identifier	    "1 Configured Video Device"
	      Driver		      "fglrx"
        BusID           "PCI:1:0:0"
        Option          "MergedFB" "False"
        Screen          0
EndSection

Section "Device"
        Identifier      "2 Configured Video Device"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "MergedFB" "False"
        Screen          1
EndSection

Section "Monitor"
	Identifier	"1 Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"2 Configured Monitor"
EndSection

Section "Screen"
	Identifier	"1 Default Screen"
	Monitor		  "1 Configured Monitor"
	Device		  "1 Configured Video Device"
	Defaultdepth	24
        SubSection      "Display"
           Depth           24
           Modes           "1280x1024"
        EndSubSection
EndSection

Section "Screen"
	Identifier	"2 Default Screen"
	Monitor		"2 Configured Monitor"
	Device		"2 Configured Video Device"
	Defaultdepth	24
        SubSection      "Display"
           Depth           24
           Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen "1 Default Screen"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
EndSection

Section "ServerLayout"
	Identifier	"Multihead"
        screen "1 Default Screen" LeftOf "2 Default Screen"
        screen "2 Default Screen" RightOf "1 Default Screen"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
EndSection

Section "ServerFlags"
	Option "xinerama" "true"
	Option "DefaultServerLayout" "Multihead"
EndSection

Section "Module"
	Load		"glx"
EndSection

Thanks for any help -- Max

---

### Post by MaxMax on 2008-06-05
I never found how to fix that title bar problem, but now I have found an alternative way to configure my dual monitor setup. Instead of Xinerama, I use Big-Desktop. 

See [http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941) 

I followed the instructions listed there and now my desktop extends over my two monitors, just as it does in MS Windows.

Hope this helps you if you have the same problem I did.

---

