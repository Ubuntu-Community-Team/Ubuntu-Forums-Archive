---
title: "3 monitors across two video cards."
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by TremerePuck on 2007-09-14
I'm trying to get a three monitor setup I'm trying to get working. The first card is a nVidia with two monitors connected to it. I have those two working using twinview. The second card is an old 3dfx Voodoo3 3000 with one monitor connected. I can't get it to come on at all. I've been trying for several days now to no avail. 

Quick review of what I want: Two monitors on nVidia using twinview. One monitor on Voodoo3 without xinerama as I will not need to be able to drag windows across. I'd like to have GL acceleration at 1024x768 @ 16 (since that's the hardware limitation)  if possible. If not, I'll live.

Here is my xorg.conf:

```

Section "Files"
    FontPath "unix/:-1"
EndSection

Section "ServerFlags"

    Option "RandR" "on"
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "/usr/X11R6/lib/modules/extensions/libglx.so"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Plug'n Play"
    HorizSync 30-70
    VertRefresh 50-120
    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
 
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Monitor"
    Identifier "monitor2"
    VendorName "Plug'n Play"
    HorizSync 30.0-69.0
    VertRefresh 50.0-120.0

    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630

    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia"
    BoardName "NVIDIA GeForce 4 (generic)"
    Driver "nvidia"
    Screen 0
    BusID "PCI:1:0:0"
    Option "DPMS"
    Option "IgnoreEDID" "1"

    Option "TwinView" "1"
    Option "Metamodes" "1280x1024,1280x1024;"
    Option "ConnectedMonitor" "DFP,DFP"
    Option "SecondMonitorHorizSync" "30-70"
    Option "SecondMonitorVertRefresh" "50-140"
    Option "NvAGP" "3"
EndSection

Section "Device"
    Identifier "device2"
    VendorName "3dfx"
    BoardName "Voodoo 3 3000"
    Driver "tdfx"
    Screen 0
    BusID "PCI:00:10:0"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
    Identifier "screen2"
    Device "device2"
    Monitor "monitor2"
    DefaultColorDepth 16

    Subsection "Display"
        Depth 8
        Virtual 1280 1024
    EndSubsection

    Subsection "Display"
        Depth 15
        Virtual 1280 1024
    EndSubsection

    Subsection "Display"
        Depth 16
        Virtual 1024 768
    EndSubsection

    Subsection "Display"
        Depth 24
        Virtual 1280 1024
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard0" "CoreKeyboard"
    InputDevice "Mouse0" "CorePointer"
    Screen "screen1"
    Screen "screen2" RightOf "screen1"
#    Option "Xinerama" 
EndSection

```

Any help is appreciated!

---

### Post by TremerePuck on 2007-09-15
Bump?

---

### Post by MrHippocampus on 2007-09-15
You should try adding the modes for the second monitor in to the second screen section, if that doesn't work have a look through /var/log/Xorg.0.log, that should give you some idea of what's going wrong.

---

### Post by TremerePuck on 2007-09-15
I found what was wrong. lspci was showing my Voodoo3 located at 00:10.0 when it is actually at 00:16.0.

 Now I have all three monitors working. Though it's impossible to have acceleration on the Voodoo with 16 bit color depth since all the screens must have the same color depth and I don't want to set them all to 16.

I don't have them working exactly as I want it though. I'm not sure if it's even possible. Right now both the monitors on the nVidia card are being treated as one big monitor, but if I disable the Voodoo screens it is treated like just an extension, with the kicker panel on one screen, and full size not spreading to both. Is there any way of getting this functionality with the three monitors?

---

### Post by MrHippocampus on 2007-09-16
The problem you describe is what happens when you have a triple-view setup with two of the screens running twinview. What you have to do is set up the screens so that they all use standard xinerama rather than twinview+xinerama, basically youll need to have 3 device, monitor and screen sections in your xorg.conf, one for each monitor.

---

### Post by clublucifer on 2007-09-16
Hi I am trying to set up 3 22" widescreen monitors on dual Nvidia DVI 8600GTS's I have done everything in the world which should get it to work with no luck! I wonder if maybe my machine too is listing the card in the wring PCI Bus it says it is in 2:0:0 and there are only two PCI express ports in the machine both gilled to the hilt with shinny new Nvidia 8600GTS's I finally got the three monitors to work in Sabayon at around 4am this morning but it is not as stable as Ubuntu

Im running FEISTY below is a copy of my xorg.conf, I have added all the extra monitor sections and device section myself using guess work, please bear with me a litttle guys only just started to get back into Linux after quite literally throwing my old machine with Micromouse Windyish in to the back garden!!

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
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
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
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
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Secondary Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:2:0:0"
    Screen          2
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1680x1050 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by MrHippocampus on 2007-09-16
ok, ive taken your xorg.conf and edited it so it *should* work as long as those PCI addresses are ok. The basic idea is to set up your xorg.conf with a montior/device/screen section for each monitor and then stitch them together in the serverlayout section.

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings: version 1.0 (buildmeister@builder3) Wed Jun 13 18:40:26 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
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
    Screen 1 "Screen1" RightOf "Screen0"
    Screen 2 "Screen2" RightOf "Screen1"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    InputDevice "stylus" "SendCoreEvents"
    InputDevice "cursor" "SendCoreEvents"
    InputDevice "eraser" "SendCoreEvents"
    Option       "Xinerama"  "on"
EndSection

Section "ServerFlags"
    Option "Xinerama" "1"
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

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "CoreKeyboard"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "gb"
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
    VendorName "Samsung"
    ModelName "Samsung SyncMaster"
    HorizSync 30.0 - 81.0
    VertRefresh 56.0 - 75.0
EndSection

Section "Monitor"
    Identifier "Monitor1"
    VendorName "Samsung"
    ModelName "Samsung SyncMaster"
    HorizSync 30.0 - 81.0
    VertRefresh 56.0 - 75.0
EndSection

Section "Monitor"
    Identifier "Monitor2"
    VendorName "Samsung"
    ModelName "Samsung SyncMaster"
    HorizSync 30.0 - 81.0
    VertRefresh 56.0 - 75.0
EndSection


Section "Device"
    Identifier "Videocard0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce 8600 GT"
    BusID "PCI:1:0:0"
    Screen 0
EndSection

Section "Device"
    Identifier "Videocard1"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce 8600 GT"
    BusID "PCI:1:0:0"
    Screen 1
EndSection

Section "Device"
    Identifier "Videocard2"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce 8600 GT"
    BusID "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Videocard0"
    Monitor "Monitor0"
    DefaultDepth 24
    
    SubSection "Display"
        Depth 16
        Modes "1680x1050" "800x600" "640x480"
    EndSubSection
    
    SubSection "Display"
        Depth 24
        Modes "1680x1050" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "Videocard1"
    Monitor "Monitor1"
    DefaultDepth 24
    
    SubSection "Display"
        Depth 16
        Modes "1680x1050" "800x600" "640x480"
    EndSubSection
    
    SubSection "Display"
        Depth 24
        Modes "1680x1050" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device "Videocard2"
    Monitor "Monitor2"
    DefaultDepth 24
    
    SubSection "Display"
        Depth 16
        Modes "1680x1050" "800x600" "640x480"
    EndSubSection
    
    SubSection "Display"
        Depth 24
        Modes "1680x1050" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

### Post by clublucifer on 2007-09-16
Thanks for your help but unfortunately it didn't work! 

These config files look pretty straight forward but they never seem to work as they should!

when i so lspci it says the second card is in pci bus 02:00:0

Not sure if this is of any benefit ti the thread but when I got it working on Sabayon I had to fiddle with the xorg.conf file but without touching anything before that the nVidia driver detected both graphic cards and all three monitors in the control panel,  it just wouldn't let me place them next to each other so I had to edit the xorg.conf manually and it worked a treat apart from compiz being rather unstable!



cheers guys!

Jamie:)

---

### Post by MrHippocampus on 2007-09-16
You should try looking at the Xserver output in /var/log/Xorg.0.log, sometimes that can give you an idea of whats going wrong.

---

### Post by clublucifer on 2007-09-16
Yeah I already looked at the log, i tried to attach it to my last post!

this is the part that it is unhappy with in the log:

(EE) NVIDIA(2): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) NVIDIA(2):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(2):     additional information.
(EE) NVIDIA(2): Failed to initialize the NVIDIA graphics device!
i

lspci identifies the card being on that bus, so I am kind of lost!

Cheers

Jamie

---

### Post by MrHippocampus on 2007-09-16
hmmm, for a problem like that you could try the nvidia linux forums [here]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"), a search there might come up with something, if not you can post about your problem (read the stickys first and generate a bug report.).

---

### Post by lime4x4 on 2007-09-16
here is copy of my working xorg file. I'm using 2 nvdia pcie cards in sli mode. I have 3 flcd panels
hope this helps.. Also i'm running each monitor as a seperate desktop

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

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
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1440 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
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
    ModelName      "DELL 2005FPW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HSD JW199D"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Gateway FPD1975W"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:10:0:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1680x1050 +0+0; 1280x1024 +0+0; 1280x960 +0+0; 1152x864 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP-0: 1440x900 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "metamodes" "DFP-1: 1440x900 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by pstracha on 2008-01-13
> **lime4x4 said:**
> here is copy of my working xorg file. I'm using 2 nvdia pcie cards in sli mode. I have 3 flcd panels
hope this helps.. Also i'm running each monitor as a seperate desktop


lime4x4, when you run seperate desktops like this can you open Firefox in all three at once? I'm not able to, that is, If I have Firefox running in one desktop and try to open it again in another I kept getting this error:

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

---

### Post by lime4x4 on 2008-01-14
Actually i expanded my setup to use 4 lcd flat panel monitors. And yes i can open firefox on each panel. I had to create a new profile for fire fox on each panel then i just changed the command firefox uses on each panel to reflect a diffrent profile.
ex
my main panel uses firefox %u to start firefox
my second panel uses firefox -P default to start firefox.
Then i use googel sycn to keep all my firefox sycned with the same bookmarks

---

### Post by pstracha on 2008-01-15
> **lime4x4 said:**
> 
my main panel uses firefox %u to start firefox
my second panel uses firefox -P default to start firefox.
Then i use googel sycn to keep all my firefox sycned with the same bookmarks

That's a very creative work around, I'll give it a try. Thank you for the tip!

---

