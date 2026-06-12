---
title: "Ubuntu 10.4 and radeonhd driver slow performances issues"
date: 2010-05-19
forum: Multimedia Software
---

### Post by puccio on 2010-05-19
Hi,

I have Dell Inspiron 6400 equipped with an **ATI Radeon Mobility X1400** card and running Ubuntu 10.4.

Before the upgrade from 9.10 to 10.4 I was using the "generic" **xserver-xorg-video-radeon**, which was working fine but after the upgraded did NOT allow me to work in Dual Screen mode.

I then saw that there is a **xserver-xorg-video-radeonhd** driver which targets, among all, my X1400 card. I installed it and the Dual Screen now indeed works but I notice that my system is slower (actually, it stresses a lot the CPU) when I do things like scrolling a page in the browser, reducing/restoring a window, etc.. so I'm wondering if it isn't a driver or configuration issue in Xorg.

My xorg.conf (regeranted from scratch by the **Xorg -configure**):

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri2"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "AccelMethod"        	# [<str>]
        #Option     "offscreensize"      	# [<str>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ignoreconnector"    	# [<str>]
        #Option     "forcereduced"       	# [<bool>]
        #Option     "forcedpi"           	# <i>
        #Option     "useconfiguredmonitor" 	# [<bool>]
        #Option     "HPD"                	# <str>
        #Option     "NoRandr"            	# [<bool>]
        #Option     "RROutputOrder"      	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "TVMode"             	# [<str>]
        #Option     "ScaleType"          	# [<str>]
        #Option     "UseAtomBIOS"        	# [<bool>]
        #Option     "AtomBIOS"           	# [<str>]
        #Option     "UnverifiedFeatures" 	# [<bool>]
        #Option     "Audio"              	# [<bool>]
        #Option     "AudioStreamSilence" 	# [<str>]
        #Option     "HDMI"               	# [<str>]
        #Option     "COHERENT"           	# [<str>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "LowPowerModeEngineClock" 	# <i>
	Identifier  "Card0"
	Driver      "radeonhd"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility X1400"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

And:
```

glxinfo | grep -i rend
direct rendering: Yes
OpenGL renderer string: Software Rasterizer

```

Thank you in advance for any support!

---

### Post by marvec on 2010-07-07
The same applies for me when I upgraded to 10.04!

radeon = no dual screen
fglrx = complete mess
radeonhd = soooo sloooow

I used radeonhd before the upgrade without any problems. What can be the issue?

---

### Post by Yellow Pasque on 2010-07-07
If you tried to install fglrx, it's possible you need to clean your system up a bit: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)
After you do that (if applicable), restart X by logging in/out and then come back and post your /var/log/Xorg.0.log file (please use [ code ][ /code ] tags as it's a large file).

---

### Post by marvec on 2010-07-07
Hello,

my system was definitely clean. I first tried radeonhd and radeon before fglrx. Nevertheless, I found a workaround.

I followed instructions in section "Building radeonhd from git Source" at [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
I also needed to add a kernel parameter radeon.modeset=0 (in /boot/grub/menu.lst). This made my system usable again.

It has a couple of drawbacks:
1) a nice graphic mode cannot be set during boot/power off phase
2) your system stability depends on what is currently in git

Since I am a perfectionist, I keep trying to find out why kernel mode setting doesn't work with the driver (any hints anyone?).

---

### Post by Yellow Pasque on 2010-07-07
> Since I am a perfectionist, I keep trying to find out why kernel mode setting doesn't work with the driver
radeonhd doesn't support KMS (radeonhd isn't being actively developed).

---

### Post by marvec on 2010-07-08
This is strange, because I used radeonhd with previous version of Ubuntu and KMS worked. Is radeonhd the same as xf86-video-radeonhd? What is actively developed nowadays? I'm little bit confused...

---

### Post by marvec on 2010-07-26
After the last update, the open source driver "radeon" started working for me. I can use multiple displays when I configure them with xrandr. Btw. my video card is ATI Technologies Inc RV516 [Radeon X1300 Pro].

---

