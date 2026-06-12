---
title: "Wider screen resolution (xorg.conf)"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by leaded on 2006-11-03
Hey everybody. I'm using an Intel i810 driver (specs sheet says Intel 950, but I haven't tried changing it yet. Xorg.conf detected 945; 950 may be the chipset?) with a Dell 2405FPW. I'm using the VGA input because my video card doesn't have DVI. 
**Edit:** dmesg reports: [17179583.720000] agpgart: Detected an Intel 945G Chipset.

Upon rebooting from installing the Ubuntu Alternate version of Edgy, my monitor wouldn't display anything (D-SUB Cannot display this mode). Same thing with another monitor. I booted up the system and plugged it into the monitor later and got it to work somewhat (it displayed a fraction of the screen and would scroll up when I moved the mouse up, weird). 

Anyway, I found some help [here](http://www.linuxquestions.org/questions/showthread.php?t=357545), but I had to tweak it a little bit. This monitor's max resolution is 1920x1200. I've got a Mac mini in the DVI port and that's the reported resolution. On Ubuntu, the highest I can get it to display is 1600x1200, putting some black bars on each side (I set the monitor so it won't scale or stretch). 

Below is my xorg.conf (edited to the relevant portions). I can't choose 1920x1200 in the System->Preferences->Screen Resolution box, only 1600x1200, 1024x768, 800x600, and 640x480 (so no widescreen ones? hmm...). Can someone help me make full use of my monitor?

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#

... clip ...

Section "Module"
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

... clip ...

Section "Monitor"
	Identifier	"DELL 2405FPW"
	ModelName	"2405FPW"
	VendorName	"Dell"
	Option		"DPMS" "CalcAlgorithm"
	Option		"CheckDesktopGeometry"
#	Display		524 321  ## Xorg says Display is not valid in the Monitor section
	HorizSync	30.0-81.0
	VertRefresh	56.0-76.0
	UseModes	"Modes[0]"
EndSection

Section "Modes"
	Identifier    "Modes[0]"
	Modeline      "1920x1200" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +Hsync -Vsync
	Modeline      "1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 +Hsync -Vsync
	Modeline      "1280x1024" 138.54 1280 1368 1504 1728 1024 1025 1028 1069 +Hsync -Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"DELL 2405FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by electricshoes on 2006-11-03
I was having the same problem in Edgy with 1440x900 res. This is what I did in my xorg for the Monitor and Screen Sections to force 1 resolution

```

Section "Monitor"
        Identifier      "VA1912wb"
        HorizSync       30.0 - 82.0
        VertRefresh     50.0 - 85.0
        Option          "DPMS"
        Modeline        "1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
        Modeline        "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
        DisplaySize     1440 900
EndSection

Section "Device"
        Identifier     "NVIDIA Corporation NVIDIA Default Card"
        Driver         "nvidia"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "VA1912wb"
        DefaultDepth    24

        SubSection      "Display"
        Depth           24
        Modes           "1440x900_70.00" "1440x900_60.00"
    EndSubSection
EndSection




```Now the only choice I will have is the res I want. Maybe something similar will help you.

---

### Post by leaded on 2006-11-03
You'll have to excuse my ignorace, but which portion is relevant? Is it that you removed all other resolutions in the SubSection, or that you added _70.00 to the Modelines? If it's the latter, what's the relevance of the number? Is it the same as the Hz in the Screen Resolution options?

Thanks for replying!

**Edit:** I just tried removing all other entries, but it still booted up to 1600x1200 and the System-Preferences-Screen Resolution window has the same options as before!!! Why is that!?

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 945G Integrated Graphics Controller"
        Monitor         "DELL 2405FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes           "1920x1200"
        EndSubSection
EndSection

```

**Edit 2:** I commented out the other two Modelines and I got the "Cannot display" message from my monitor. :( I also tried adding a _60 to the end of 1920x1200 in both the Modeline and the SubSection (because my Mac mini says it's 1920x1200 at 60Hz) but it still didn't work.

---

### Post by electricshoes on 2006-11-03
The Modeline in the Monitor section is whats important.
What does your monitor section look like ?

---

### Post by leaded on 2006-11-03
Section "Monitor"
	Identifier	"DELL 2405FPW"
	ModelName	"2405FPW"
	VendorName	"Dell"
	Option		"DPMS" "CalcAlgorithm"
	Option		"CheckDesktopGeometry"
#	Display		524 321  ## Xorg says Display is not valid in the Monitor section
	HorizSync	30.0-81.0
	VertRefresh	56.0-76.0
	UseModes	"Modes[0]"
EndSection

---

### Post by electricshoes on 2006-11-03
```
sudo dpkg-reconfigure xserver-xorg
```Do that and let it re-setup your xorg.

Do you know what Hsync and Vsync your monitor will do ?

---

### Post by pinkcanvas on 2007-09-20
This is my first post but I have been lurking around for a while because I have a similar problem. My xorg.conf bears no relation to the options available using the Screen Resolution menu. Does anyone else have some light to shed on this? I have done the xorg.conf edits as outlined, placing a modeline generated at [http://xtiming.sourceforge.net](http://xtiming.sourceforge.net) in the monitor section but it still blithely lists the four basic resolutions, not the 1360x768 that my LCD TV needs. Trying to build a nice little media box here but just getting nowhere! My graphics card is the Intel 845g onboard chipset. So quite nasty really but it should support this I believe. 
Any help greatly appreciated.

---

### Post by zavizionov on 2007-10-12
[http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html](http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html)

---

