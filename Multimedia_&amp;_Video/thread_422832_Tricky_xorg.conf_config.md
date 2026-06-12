---
title: "Tricky xorg.conf config"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by TomTheGeek on 2007-04-25
I'm on Ubuntu 7.04 and I have a pretty weird screen configuration that I could use some help with.

I have 2 Nvidia cards, a PCI geforce 5200 and an AGP geforce 5500.

I have 4 screens, two 17" CRT's @ 1024x768, a 19" LCD @ 1280x1024 and a TV at normal TV resolution.

I have the two 17" CRTs connected to the PCI 5200

I have the 19" LCD connected to the DVI on the 5500 and the TV is hooked up to the svideo on the 5500 also.

The layout on my desk is CRT, LCD, CRT then a long cable to the TV.

I want all three monitors on my desk to be one big desktop with the LCD as the primary monitor with the task bar and all that. I want to be able to drag windows across all three monitors. The TV I would like to be a clone of the LCD but it can be a monitor all by itself just so I can play movies on it full screen.

I'm using the nvidia restricted driver.

here's the relavent parts of my xorg.conf 

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen "Screen0" LeftOf "Screen1"
    Screen "Screen1" LeftOf "Screen2"
    Screen "Screen2" 0 0
    Option "Xinerama" "true"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
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
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "vbe"
    Load  "dri"
    Load  "GLcore"
    Load  "record"
    Load  "dbe"
    Load  "xtrap"
    Load  "type1"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "NEC"
	ModelName    "MultiSync FE700"
        HorizSync    31.0 - 81.0
        VertRefresh  55.0 - 85.0
        Option       "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "AG Neovo"
	ModelName    "F-419"
        Option       "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "NEC"
	ModelName    "MultiSync FE700"
        HorizSync    31.0 - 81.0
        VertRefresh  55.0 - 85.0
        Option       "DPMS"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "NV34 [GeForce FX 5500]"
	Option      "ConnectedMonitor" "FPD"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "NV34 [GeForce FX 5200]"
	Option      "TwinView" "true"
	Option      "SecondMonitorHorizSync" "31-81"
	Option      "SecondMonitorVertRefresh" "55-85"
	Option      "MetaModes" "1024x768,1024x768"
	Option      "ConnectedMonitor" "CRT,CRT"
	BusID       "PCI:1:7:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card1"
    Monitor    "Monitor0"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card0"
    Monitor    "Monitor1"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card1"
    Monitor    "Monitor2"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

#Section "Extensions"
#    Option         "Composite" "Enable"
#EndSection

```

---

### Post by TomTheGeek on 2007-06-24
I finally got my screen configured, what I was looking for was this

```
sudo /usr/bin/nvidia-settings
```

That makes it very easy to configure multiple screens. Just drag them around until they are where you want them. Simple. 

Now if they would only make this a shortcut in the settings menu.

---

