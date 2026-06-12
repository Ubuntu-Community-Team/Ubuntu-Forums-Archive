---
title: "problem with tv out nvidia with svideo"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by nephish on 2007-08-23
hello there all, 
i followed the wiki in community docs to get a second screen that is my tv. 
i am using an nvidia GeForce FX 5200 that does great in ubuntu so far, desktop cube and whatnot. but i cant seem to get the svideo out working. 

the xorg log tells me that it cannot find a monitor for screen1 ( the tv out )
does it actually probe the ports on the video card for something being connected ?

i ask that because i am using a little adapter to convert the svideo to rca ( the yellow ) cable because my tv does not have svideo input. 

do i need to get a different type of adapter ? or will this just not work at all if the signal is not found on the video card ?

thanks

---

### Post by tseliot on 2007-08-24
type:
```
sudo nvidia-settings
```

and enable the tvout from there

---

### Post by nephish on 2007-08-24
wow, thanks for that. 
i have the package nvidia-settings installed, but cannot figure out from there how to enable
tv-out. It doesn't seem to show up as an option.

how do enable tv-out from nvidia-settings.

thanks again

---

### Post by tseliot on 2007-08-24
click on X Server Display configuration and set up the tvout from there

---

### Post by nephish on 2007-08-24
ok , will do when i get back to the house. 
thanks very much for your help.

---

### Post by nephish on 2007-08-24
ok, all i am seeing is the screen0 and default display ( the monitor ) 
the following is my xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection



Section "Device" # Dell
	Identifier	"Device0"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Screen 0
EndSection

Section "Device" # TV
   	Driver          "nvidia" 
   	Identifier      "Device1" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO"
   	Option          "TVStandard" "NTSC-M" 
   	Option          "ConnectedMonitor" "TV" 
        BusID           "PCI:1:0:0" 
EndSection

Section "Monitor" 
	Identifier "DellMonitor" 
	Option		"DPMS"
EndSection

Section "Monitor" # TV
    Identifier "Television" #TV 
    HorizSync 30-50
    VertRefresh 50 
EndSection

Section "Screen"
	Identifier  "Screen0" 
   	Device      "Device0" 
   	Monitor     "DellMonitor"

	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "NTSC-M"
                SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection


Section "ServerLayout" 
   	Identifier  "Simple Layout" 
       	Screen 0 "Screen0" 
       	Screen 1 "Screen1" rightof "Screen0" 
   	InputDevice "Configured Mouse" "CorePointer" 
   	InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection


Section "DRI"
	Mode	0666
EndSection
```

thanks for your help on this

---

### Post by nephish on 2007-08-27
OK, trying it now with only one screen like in the community documentation, but trying to apply what i have learned in this thread. here is my xorg.conf.
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection



Section "Device" # Dell
	Identifier	"Device0"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Screen 0
EndSection

Section "Monitor" 
	Identifier "DellMonitor" 
	Option		"DPMS"
EndSection


Section "Screen"
    Identifier  "Screen 1"
    Device      "Device0"
    Monitor     "DellMonitor"
    DefaultDepth 24
    Option      "RenderAccel"            "True"
    Option      "AllowGLXWithComposite"  "True"
    Option      "AddARGBGLXVisuals"      "True"
    Option      "DisableGLXRootClipping" "True"
    Option      "TwinView"               "1"
    Option      "metamodes"              "CRT: 1280x1024 +0+0, TV: 1024x768 +0+0"
    Option  "TVOutFormat" "SVIDEO"
    Option  "TVStandard" "NTSC-M"
    Option      "SecondMonitorHorizSync" "30-50"
    Option      "SecondMonitorVertRefresh" "60"
   Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection


Section "ServerLayout"
    Identifier  "Simple Layout"
    Screen "Screen 1"
    InputDevice "Configured Mouse" "CorePointer" 
    InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection



Section "DRI"
	Mode	0666
EndSection
```

Is there anything obviously wrong?

by the way, i am using a tv with composite in, but my nvidia card is svideo out, i am running it through a converter. Does this make a difference ? 
thanks

---

### Post by xpod on 2007-08-28
Not sure if you got yours fixed nephish but i`ll bump it for you as i`m also now having a strange problem with the TVout and the below guide might help you a bit if your current methods are not working:)

I always use  [This guide](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition) with the MX4000 i have as doing things via the nvidia settings never quite works for me.

I was recently given a new 19" flat screen monitor and after doing a fresh installation of feisty and setting up the new TVout settings the mouse pointer will no longer move over to the TV screen, which does have  the second desktop ok.

I cant really see any problem in the xorg.conf myself and have even tried leftof,Leftof,rightof and Rightof as far as the actual screen positioning is concerend,all to no avail.(i read that worked for someone else somewhere)

This is the relevant parts of the xorg.conf
```
Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	Busid		"PCI:0:10:0"
        Screen 0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device" 
        Driver          "nvidia" 
        Identifier      "Device[1]" 
        Screen 1 
        Option          "TVOutFormat" "SVIDEO" #or Composite etc 
        Option          "TVStandard" "PAL-G" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:0:10:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #Primary display
	Option		"DPMS"
        HorizSync        31-83
        VertRefresh      56-75
EndSection

Section "Monitor"
        Identifier       "Monitor[1]"  #TV
        HorizSync         30-50
        VertRefresh       60
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x900"	"1280x1024"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen" 
        Device "Device[1]" 
        Identifier "Screen[1]" 
        Monitor "Monitor[1]" 
        DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1024x728_60" 
        EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
        screen 0 "Screen[0]"
        Screen 1 "Screen[1]" leftof  "screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
EndSection
```

Everything is  fine bar the mouse pointer refusing to cross over:confused:

---

### Post by nephish on 2007-08-28
hey there, thanks for the bump, the link you posted is the first thing i tried, and what i keep going back to since its easy to follow.

i cannot even get the tv to come on, weird, but x gives me no errors on startup 
thanks again

---

### Post by Caremon on 2008-05-11
> **tseliot said:**
> type:
```
sudo nvidia-settings
```

and enable the tvout from there
Thanks 

I whas woundering why the nvidia-settings is not with the restrigted nvidia package. It woud help normal windows users to use linux.

But i did spend 5 minutes to find this and it works really good :D Thing are gettin really easy by the years 

Thanks

---

