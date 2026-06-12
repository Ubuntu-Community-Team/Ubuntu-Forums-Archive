---
title: "How do you change primary monitor?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Skeorx13 on 2007-06-28
I have a problem with my dual monitor setup. I have one 19" monitor and one 15" monitor to the right. I have set up twinview to make one desktop out of it. However, the small screen is, for some reason, set as my primary monitor. I would like to be able to have my 19" monitor set as the primary screen. This has been causing problems when viewing videos as the fullscreen mode always sends the full screen to my small monitor, not the large one where I would like it to be. I figured I could just change the ordering of the monitors in my xorg.conf file, but the horizontal refresh and vsync rates aren't identical and I don't want to fry my monitors. I am also incapable of switching the plug positions in my graphics card because I have a watercooling radiator in the way and my small monitor has a CRT to DVI adapter attached to it. I tried messing with nvidia-settings but I can't figure out how to swap the monitor priority. This has also been annoying because my login screen goes to the small screen instead of the large one as well. Does anyone have some insight to alleviate my annoyances?

My xorg.conf for reference:
Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Default Screen [0]" 0 0
Screen 1 "Default Screen [1]" RightOf "Default Screen [0]"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "Radius [0]"
Option "DPMS"
HorizSync 30-60
VertRefresh 55-75
EndSection

Section "Monitor"
Identifier "ViewEra [1]"
Option "DPMS"
HorizSync 30-81
VertRefresh 55-75
EndSection

Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card0"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card1"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "Default Screen [0]"
Device "NVIDIA Corporation NVIDIA Default Card0"
Monitor "Radius [0]"
DefaultDepth 24
Option "Twinview" "True"
Option "TwinViewOrientation" "LeftOf"
Option "SecondMonitorHorizSync" "30-81"
Option "SecondMonitorVertRefresh" "55-75"
Option "NvAGP" "1"
Option "HWCursor" "0"
Option "SWCursor" "1"
Option "NoLogo" "False"
Option "RenderAccel" "True"
Option "MetaModes" "1024x768,1280x1024; 1024x768,1024x768; 800x600,800x600; 640x480,640x480; null,1280x1024; null,1024x768; null,800x600; null,640x480; 1024x768,null; 800x600,null; 640x480,null"
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Default Screen [1]"
Device "NVIDIA Corporation NVIDIA Default Card1"
Monitor "ViewEra [1]"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by maku-d on 2007-06-30
I've had this problem before- here's how I fixed it-

In the 'screen' section of your xorg.conf (I'd probably put it under your line- Option "TwinViewOrientation" "LeftOf") add the line-

```
Option      "TwinViewXineramaInfoOrder" "DFP"
```

Now press ctrl+alt+backspace and it should reload with the login screen on the lcd rather than crt monitor.

Hope it works (if it doesn't just press ctrl+alt+f1 then login and re-edit your xorg.conf- removing the line you added). 

Enjoy!

---

### Post by RTrev on 2007-06-30
It's too bad you can't switch the monitor cables, as I found that the primary monitor was the left jack (facing it from the back of the machine.)

---

### Post by maku-d on 2007-06-30
That won't work because regardless of where the monitors plug in they are detected in the order- 

"CRT,DFP,TV" (analog TFTs are treated as CRT)

The way to change this is to use the line above.

---

### Post by Skeorx13 on 2007-07-02
Awesome, I'll try that out when I get home and post the results.

---

### Post by robhilken on 2007-07-07
I have the same issue but my xorg.conf file is slightly different (only one screen specified) so I'm not sure where to add the line you suggest. Both my monitors are plugged into the same graphics card - one in the dvi socket the other in the rgb. I need the dvi one to be my primary monitor.

Here's my file:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Iiyama LS902U"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: 1280x1024 +0+0; CRT: 1280x960 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by mchaggis211 on 2007-07-07
thnks this solution worked but if its not to hard can someone tell me how to run fullscreen games such as x-moto on only one monitor instead of it bien strethed across both

thnks my 
x11 is :
[B]# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E173FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GS"
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
Option      "TwinViewXineramaInfoOrder" "DFP"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024_60 +0+0, DFP: 1280x1024_60 +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection[/B]

---

### Post by RTrev on 2007-07-07
I've never been completely certain what xinerama does, but I think it does precisely what you are asking for; constraining a full-screen window to just one monitor or the other.  And you probably didn't turn it off without good reason, so I'm puzzled.  But that's all that comes to mind.. you need that xinerama feature.  I was told not to do anything with it, and it would come on by itself, and that's what's always happened.

HTH...

Bob

---

### Post by Bif Powell on 2007-07-27
I have a Viewsonic LCD plugged into DVI and a DELL LCD plugged into an analog adapter (NVIDIA 6800GT with two DVI outputs).  I would like my Viewsonic to be primary.

I'm having this problem as well, but the fix above (    Option         "TwinViewXineramaInfoOrder" "DFP") does not appear to change anything for me.

I used ENVY to install my drivers, I used nvidia-settings to setup my dual display.

Here is my xorg.conf - many thanks for any guidance you can provide:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:50 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:14 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Dell E193FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Series GPU]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:7:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Series GPU]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
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
    Option         "TwinViewXineramaInfoOrder" "DFP"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by RTrev on 2007-07-27
It looks like you have deliberately turned Twinview **off**.  I thought you would need that enabled for any of the other "rightof", "leftof", sorts of commands to work?

---

### Post by Bif Powell on 2007-07-27
Everything about my configuration (video-wise anyways) is working properly, except the wrong display is primary.  I don't really know what twinview is so while that's somewhat informative, I do not know how to proceed - or are you saying I'm stuck this way?  Are there any trouble-shooting steps you can recommend from this point?

Thanks!

---

### Post by MrHippocampus on 2007-07-27
Looks like youve set up your dual screens using xinerama rather than twinview, that means the TwinViewXineramaInfoOrder wont work as its only for twinview setups.

This might work for your setup, not sure though, replace your existing serverlayout section with the one below

```

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen1" RightOf "Screen0"
Screen 1 "Screen0" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

```

---

### Post by Bif Powell on 2007-07-27
Should I remove the InfoOrder entry?  What is twinview, is that preferable to how I'm running now?  Will the decision to NOT use twinview effect my ability to run wine and play windows video games?  Many thanks!

---

### Post by MrHippocampus on 2007-07-27
Basically, twinview is nvidia's own implentation of dual screens, its designed to be done on a single graphics card with two screens connected to it. Xinerama is more general and can work with merging screens on totally separate graphics cards. When twinview first came out it was much faster and had less problems than standard xinerama across a dual head graphics card (although today the difference is no longer that great).

Anyway, the vast majority of people on the forums run twinview setups and if your just running on a single card with two heads then twinview is probably the way to go as it should give you a bit of a performance boost :D


If you want to switch to twinview, first back up your xorg.conf somewhere (and know how to put it back via the command line if anything goes wrong).
Then run "sudo nvidia-settings" and configure your screens via the display configuation page. Configure the screens to use twinview rather than xinerama (configure button), then  when your done press save to configuration file and restart the X server with Ctrl+Alt+Backspace.

 If it works you should have the log in screen, if it doesnt then youll need to replace /etc/X11/xorg.conf with your backup and post what went wrong :)

---

### Post by Bif Powell on 2007-07-27
> **MrHippocampus said:**
> Looks like youve set up your dual screens using xinerama rather than twinview, that means the TwinViewXineramaInfoOrder wont work as its only for twinview setups.

This might work for your setup, not sure though, replace your existing serverlayout section with the one below

```

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen1" RightOf "Screen0"
Screen 1 "Screen0" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

```

This worked for me (changed RightOf to LeftOf, but I got the idea.  Many thanks.  Still curious what twinview is (edit: simultaneous post, thanks for the twinview primer), but I'll check around.  Many thanks! :KS

---

### Post by Bif Powell on 2007-07-27
> **MrHippocampus said:**
> Basically, twinview is nvidia's own implentation of dual screens, its designed to be done on a single graphics card with two screens connected to it. Xinerama is more general and can work with merging screens on totally separate graphics cards. When twinview first came out it was much faster and had less problems than standard xinerama across a dual head graphics card (although today the difference is no longer that great).

Anyway, the vast majority of people on the forums run twinview setups and if your just running on a single card with two heads then twinview is probably the way to go as it should give you a bit of a performance boost :D


If you want to switch to twinview, first back up your xorg.conf somewhere (and know how to put it back via the command line if anything goes wrong).
Then run "sudo nvidia-settings" and configure your screens via the display configuation page. Configure the screens to use twinview rather than xinerama (configure button), then  when your done press save to configuration file and restart the X server with Ctrl+Alt+Backspace.

 If it works you should have the log in screen, if it doesnt then youll need to replace /etc/X11/xorg.conf with your backup and post what went wrong :)

I found the twinview setting (up until now I thought it was a program, but it's just a setting - many thanks for clearing that up) and I'm using it currently - all other things being equal, I would just assume do what is most common around the ubuntu circles, however my analog is still primary.

They obviously need a check-box to allow you to select which is primary in nvidia-settings.

Anyways, here is my xorg.conf, and further assistance appreciated!

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:50 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:14 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Dell E193FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Series GPU]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Series GPU]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP"
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

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: 1280x1024 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
# Removed Option "metamodes" "CRT: 1280x1024 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by MrHippocampus on 2007-07-27
ok, your xorg.conf had a lot of stuff in it, a fair bit of it wasn't doing anything useful so i've gotten rid of the useless bits and left only the bits you should need :)

Again make sure you have a backup to use in case this one fails.
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings: version 1.0 (buildmeister@builder26) Wed Jun 13 16:54:50 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig: version 1.0 (buildmeister@builder26) Wed Jun 13 16:54:14 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "1"
Option "Xinerama" "0"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier "Monitor0"
    VendorName "Unknown"
    ModelName "Dell E193FP"
    HorizSync 30.0 - 83.0
    VertRefresh 56.0 - 76.0
EndSection

Section "Device"
    Identifier "Videocard0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce 6800 Ultra"
    #this line fixes a possible bug
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    # Removed Option "TwinView" "0"
    # Removed Option "metamodes" "CRT: 1280x1024 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    # Removed Option "metamodes" "CRT: 1280x1024 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    Identifier "Screen0"
    Device "Videocard0"
    Monitor "Monitor0"
    DefaultDepth 24
    
    #we want twinview :)
    Option "TwinView" "1"
    
    #set the flat screen to be the primary display
    Option "TwinViewXineramaInfoOrder" "DFP,CRT"
    
    #resolutions
    Option "metamodes" "CRT: 1280x1024 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"

    #Here as backup so you get something on the screen even if your not using
    #the nvidia driver
    SubSection "Display"
        Depth 16
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

### Post by Bif Powell on 2007-07-27
That was the one!  Thanks.

---

### Post by RTrev on 2007-07-27
Bif,

Glad you got it working!  I'd have given you more to go on if I'd known it.. but all I knew was that it looked odd having turned off Twinview as that's what I thought made all of this work.  <g>

As for the Xinerama, I'm confused.  Looking at my xorg log file, it seems that I'm running both Twinview **and** Xinerama:

```

(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "dfp, dfp"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
(**) NVIDIA(0): Option "Coolbits" "1"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "dfp, dfp"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.50.55
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:5:0:0:
(--) NVIDIA(0):     ViewSonic Q20wb (DFP-0)
(--) NVIDIA(0):     ViewSonic Q20wb (DFP-1)
(--) NVIDIA(0): ViewSonic Q20wb (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): ViewSonic Q20wb (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): ViewSonic Q20wb (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): ViewSonic Q20wb (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select,nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 3360 x 1050
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

<skipped a bunch of stuff here>

(II) NVIDIA(0): Setting mode "nvidia-auto-select,nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX

```

Is there any point to running both, or do I have all kinds of things here that aren't needed?  I don't understand what a tenth of this stuff is.. but it works.  I just wonder if it might work better some other way?

Thanks,
Bob

---

### Post by MrHippocampus on 2007-07-28
Looks to me like your only running twinview, the Xinerama messages your seeing look like there just saying that xinerama been initialised, but all the dual screen information seems to be coming from the nvidia driver which means you are using twinview :)

---

### Post by RTrev on 2007-07-28
> **MrHippocampus said:**
> Looks to me like your only running twinview, the Xinerama messages your seeing look like there just saying that xinerama been initialised, but all the dual screen information seems to be coming from the nvidia driver which means you are using twinview :)

Thanks!  This stuff isn't for the faint of heart.  :)

---

### Post by JustinForce on 2007-08-27
> **maku-d said:**
> 
```
Option      "TwinViewXineramaInfoOrder" "DFP"
```


This completely worked for me. Thanks!

---

### Post by turboxs on 2007-09-07
> **maku-d said:**
> I've had this problem before- here's how I fixed it-

In the 'screen' section of your xorg.conf (I'd probably put it under your line- Option "TwinViewOrientation" "LeftOf") add the line-

```
Option      "TwinViewXineramaInfoOrder" "DFP"
```

Now press ctrl+alt+backspace and it should reload with the login screen on the lcd rather than crt monitor.

Hope it works (if it doesn't just press ctrl+alt+f1 then login and re-edit your xorg.conf- removing the line you added). 

Enjoy!

Worked perfect for me, thanks bunches and bunches !!!

---

### Post by Lord C on 2007-10-23
> **maku-d said:**
> I've had this problem before- here's how I fixed it-

In the 'screen' section of your xorg.conf (I'd probably put it under your line- Option "TwinViewOrientation" "LeftOf") add the line-

```
Option      "TwinViewXineramaInfoOrder" "DFP"
```

Now press ctrl+alt+backspace and it should reload with the login screen on the lcd rather than crt monitor.

Hope it works (if it doesn't just press ctrl+alt+f1 then login and re-edit your xorg.conf- removing the line you added). 

Enjoy!

This seems to have worked.
The login screen is now on the left monitor (where i like it), but for some reason, when I maxmise games (ie UT2004), they still maxmize to the right screen. Any idea why this is?

[Edit]
Found a similar thread, helped a little [http://ubuntuforums.org/showthread.php?t=475943&highlight=dual+display+full+screen](http://ubuntuforums.org/showthread.php?t=475943&highlight=dual+display+full+screen)

Improvised, ended up changing:
>     Option         "metamodes" "CRT: 1280x1024 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 1280x960 +0+0; CRT: 1280x800 +0+0; CRT: 1152x864 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
EndSection

to:
>     Option         "metamodes" "DFP: nvidia-auto-select +0+0, CRT: 1280x1024 +1680+0; DFP: 1280x960 +0+0; DFP: 1280x800 +0+0; DFP: 1152x864 +0+0; DFP: 1024x768 +0+0; DFP: 832x624 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
    Option         "TwinViewXineramaInfoOrder" "DFP, CRT"
    Option         "UseDisplayDevice" "DFP, CRT"
    Option         "TwinViewOrientation" "DFP LeftOf CRT"
EndSection

=]

---

