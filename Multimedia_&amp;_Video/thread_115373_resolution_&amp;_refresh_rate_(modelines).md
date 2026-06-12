---
title: "resolution &amp; refresh rate (modelines?)"
date: 2006-01-10
forum: Multimedia &amp; Video
---

### Post by fangorious on 2006-01-10
I have an HP nw8240 laptop with an Ati Fire GL V5000. I followed the HOWTO to build deb packages with the latest binary drivers (8.20.8 I think), and that worked pretty well. The range of resolutions and refresh rates I can select in Screen Resolution Preferences has stuff missing though. Under windows, I can have a refresh rate up to 100, I'd be fine with 75, but I only get one choice: 60. As far as resolution. As far as resolution goes, Screen Resolution Preferences only lists one widescreen resolution: 1920x1200. I would like to use 1680x1050 (which I use under Windows). 

These are the resolutions I have in my xorg.conf (for all color depths)

"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"

Here's the resolutions I can select in the Screen Resolution Preferences

"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "1920x1080"

No idea why 1920x1080 is listed after 640x480. Only one Modeline was put in xorg.conf, and I commented it out

#Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841

And I have the HorizSyn set to 31.5-91.1 and the VertRefresh set to 60-100 (per the HP documentation for installing Linux).

---

### Post by fifteen on 2006-04-07
I have the same problem. I also use nw8240 and would like to use other widescreen resolution (1280x768 in my case) than 1920x1200

---

### Post by fangorious on 2006-04-07
see [here]("http://ubuntuforums.org/showthread.php?p=782702#post782702") for some modeline generators and create modelines for the resolutions you want at 60 Hz. Here's my xorg.conf which supports 1680x1050 and 1440x900 (also compiz+xgl and mouse thumb buttons in firefox)

> 
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc.Mobility FireGL v5000"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "KernelModuleParm"      "agplock=0"
EndSection

Section "Monitor"
        Identifier      "Samsung LCD"
        Option          "DPMS"
        HorizSync       31.5-91.1
        VertRefresh     60-100
        Modeline        "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
        Modeline        "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc.Mobility FireGL v5000"
        Monitor         "Samsung LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1920x1200" "1680x1050@60" "1600x1200" "1440x900@60" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200" "1680x1050@60" "1600x1200" "1440x900@60" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" "1680x1050@60" "1600x1200" "1440x900@60" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


---

### Post by munja on 2007-07-25
Hi,

I have a problem setting up resolution and refresh rate for my monitor (HP1740). I want it to be 1280x1024 at 60 Hz. Refresh ranges for this monitor are - horizontaly 30-83 and verticaly 56-76. i've tried to reconfigure xorg.conf however it keeps showing my desktop at 1024x768 at 51 Hz. Also I tried configuring it manually, still doesn't work, I get either a black screen or an unusable graphic interface. Tried it with modeline, also nothing. 

If anyone can help me I would apreciate it very much :)

Here is my xorg.conf file:

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
	Option		"XkbLayout"	"hr"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-50
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1280x0"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1280x0"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1280x0"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1280x0"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1280x0"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1280x0"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by MrHippocampus on 2007-07-25
@munja,

Try changing your "monitor" section to this:

```

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Horizsync 30-83
Vertrefresh 56-76
EndSection

```

And when you check the resolution and refresh rates, use the nvidia-settings program, the one your currently using shows the wrong Hz values when using the nvidia driver, nvidia-settings will tell you whats really going on.

---

### Post by munja on 2007-07-25
Thanks, I changed the "Monitor" section and checked the nvidia-settings. It seems that my monitor is detected as CRT and it shuld be LCD... 

Any ideas on how to fix it?

---

### Post by MrHippocampus on 2007-07-25
If your LCD is using a VGA cable then it will be displayed as a CRT, there is nothing you can do about this.

---

### Post by munja on 2007-07-25
Ok, yes it's a VGA cable. Well anyway I changed the resolution and refresh rate to 1280x1024 at 60 Hz  in the nvidia-settings program and now it's working, but I don't have full functionality of the graphical interface (e.g. can't open termial, have to do Ctrl+Alt+F1 to get the terminal).

Here's how relevant sections in xorg.conf look like now:

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP L1740"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0; CRT: 1280x1024_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by MrHippocampus on 2007-07-25
I think ive seen this problem before on the forums, try searching around and see if you find anything.

---

### Post by munja on 2007-07-25
Ok, thanks I'll look it up :)

---

