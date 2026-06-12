---
title: "Movie across dual screens?"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by earobinson on 2006-08-01
I have my dual screen setup working perfect under ubuntu, my problem is that i cant seem to watch a movie in both screens. I can watch the movie on screen 1 or screen 2 but not on screen1 and 2 at the same time (one half is always blue)

Will post screenshots soon.

Any ideas?

Edit: Screenshots [http://picasaweb.google.com/earobinson/UbuntuBugs](http://picasaweb.google.com/earobinson/UbuntuBugs)

---

### Post by Ziox on 2006-08-01
> **earobinson said:**
> I have my dual screen setup working perfect under ubuntu, my problem is that i cant seem to watch a movie in both screens. I can watch the movie on screen 1 or screen 2 but not on screen1 and 2 at the same time (one half is always blue)

Will post screenshots soon.

Any ideas?

are you using xinerama or twinview or mergedFB? I'm not sure about this, but perhaps DRI is needed to watch video on the second screen...

---

### Post by earobinson on 2006-08-01
> **Ziox said:**
> are you using xinerama or twinview or mergedFB? I'm not sure about this, but perhaps DRI is needed to watch video on the second screen...

I am using xinerama, and am not sure what DRI is, is there any difference between mergeFB and xinerama?

---

### Post by earobinson on 2006-08-01
My current DRI in xorg.conf looks like this
```

Section "DRI"
        Mode    0666

```

---

### Post by Ziox on 2006-08-01
> **earobinson said:**
> I am using xinerama, and am not sure what DRI is, is there any difference between mergeFB and xinerama?

Yeah Xinerama doesn't allow DRI on the second screen, but MergedFB does allow DRI...I have a howto that might help (it's in my signature if you want to check it out)

DRI is direct rendering...3d acceleration, which makes the desktop more responsive, but i'm not sure if that would help your problem :confused:

---

### Post by earobinson on 2006-08-01
Dont seem to I have tried this
```

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
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	#Option		"MergedFB"		"true"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
	#Option		"MergedFB"		"true"
        Screen 0
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	#Option		"MergedFB"		"true"
        Screen 1
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "Clone" "true"
        Option          "CloneRefresh" "85"
        Option          "MonitorLayout" "CRT,LFP"
	#Option		"MergedFB"		"true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync       30-90
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen 0        "LCD Screen Of Separate" 0 0
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "ServerLayout"
        Identifier      "SeparateHeads"
        Screen 0        "LCD Screen Of Separate" 0 0
        Screen 1        "CRT Screen Of Separate" LeftOf "LCD Screen Of Separate"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
	Option          "Xinerama" "true"
EndSection

#Section "ServerLayout"
#        Identifier      "CloneHeads"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "DRI"
        Mode    0666
EndSection

```

and this
```

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
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	Option		"MergedFB"		"true"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
	Option		"MergedFB"		"true"
        Screen 0
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	Option		"MergedFB"		"true"
        Screen 1
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "Clone" "true"
        Option          "CloneRefresh" "85"
        Option          "MonitorLayout" "CRT,LFP"
	Option		"MergedFB"		"true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync       30-90
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen 0        "LCD Screen Of Separate" 0 0
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "ServerLayout"
        Identifier      "SeparateHeads"
        Screen 0        "LCD Screen Of Separate" 0 0
        Screen 1        "CRT Screen Of Separate" LeftOf "LCD Screen Of Separate"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
	#Option          "Xinerama" "true"
EndSection

#Section "ServerLayout"
#        Identifier      "CloneHeads"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "DRI"
        Mode    0666
EndSection

```

With no luck :(

---

### Post by Ziox on 2006-08-01
> **earobinson said:**
> Dont seem to I have tried this
```

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
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	#Option		"MergedFB"		"true"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
	#Option		"MergedFB"		"true"
        Screen 0
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	#Option		"MergedFB"		"true"
        Screen 1
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "Clone" "true"
        Option          "CloneRefresh" "85"
        Option          "MonitorLayout" "CRT,LFP"
	#Option		"MergedFB"		"true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync       30-90
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen 0        "LCD Screen Of Separate" 0 0
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "ServerLayout"
        Identifier      "SeparateHeads"
        Screen 0        "LCD Screen Of Separate" 0 0
        Screen 1        "CRT Screen Of Separate" LeftOf "LCD Screen Of Separate"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
	Option          "Xinerama" "true"
EndSection

#Section "ServerLayout"
#        Identifier      "CloneHeads"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "DRI"
        Mode    0666
EndSection

```

and this
```

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
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	Option		"MergedFB"		"true"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
	Option		"MergedFB"		"true"
        Screen 0
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Driver          "i810"
        BusID           "PCI:0:2:0"
	Option		"MergedFB"		"true"
        Screen 1
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "Clone" "true"
        Option          "CloneRefresh" "85"
        Option          "MonitorLayout" "CRT,LFP"
	Option		"MergedFB"		"true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync       30-90
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for LCD of Separate"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Separate"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for CRT of Separate"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "CRT Screen Of Clone"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller for Clone"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

#Section "ServerLayout"
#        Identifier      "DefaultLayout"
#        Screen 0        "LCD Screen Of Separate" 0 0
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "ServerLayout"
        Identifier      "SeparateHeads"
        Screen 0        "LCD Screen Of Separate" 0 0
        Screen 1        "CRT Screen Of Separate" LeftOf "LCD Screen Of Separate"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
	#Option          "Xinerama" "true"
EndSection

#Section "ServerLayout"
#        Identifier      "CloneHeads"
#        Screen          "LCD Screen Of Clone"
#        Screen          "CRT Screen Of Clone"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#        InputDevice     "Synaptics Touchpad"
#EndSection

Section "DRI"
        Mode    0666
EndSection

```

With no luck :(

I have a question...How many monitors do you have?

and also, it seems like xinerama isn't on...but maybe i've read wrong...

I should also add that Xinerama isn't perfect, and watching movies or playing games over two screens isn't one of the perfect points of Xinerama

---

### Post by earobinson on 2006-08-01
Got it to work with ```
xine -F -V xshm rocket.avi
``` Thanks for all the help

---

