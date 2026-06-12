---
title: "TV out, Bottom and right out of the screen"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by feydreva on 2008-03-18
Hello, 

I have a Nvidia 6800
I use the VGA for my screen, and the DVI goes to the HDMI TV.
the TV is HDTV 1920x1080i / 1280x720p

I have a nice image on the TV, my only problem, is the Top, the Left, and the Bottom are a little bit ut of the screen...

How can I solve that ?

Fey

---

### Post by feydreva on 2008-03-18
xorg.conf: 


Section "ServerLayout"
    Identifier     "Simple Layout"
    Screen 0       "Screen[0]"
    Screen 1       "Screen[1]" RightOf "Screen[0]"
    InputDevice     "Configured Mouse" "CorePointer"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
Endsection

Section "Files"
	# path to defoma fonts
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
    FontPath        "/usr/share/fonts/truetype"
    FontPath        "/usr/local/share/fonts/truetype"
    FontPath        "/usr/lib/X11/fonts/CID"
    FontPath        "/usr/lib/X11/fonts/Speedo"
    FontPath        "/usr/lib/X11/fonts/misc"
    FontPath        "/usr/lib/X11/fonts/cyrillic"
    FontPath        "/usr/lib/X11/fonts/100dpi:unscaled"
    FontPath        "/usr/lib/X11/fonts/75dpi:unscaled"
    FontPath        "/usr/lib/X11/fonts/Type1"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/X11R6/lib/X11/fonts/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
EndSection

Section "Monitor"
    Identifier     "Monitor[0]" #samsung syncmaster 173B computeur screen
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor[1]" #TV
    HorizSync 30-50
    VertRefresh 60
EndSection
  
Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    screen 0
EndSection

Section "Device"
    Identifier     "Device[1]"
    Driver         "nvidia"
    screen 1
    Option          "TVOutFormat" "Composite" #or SVIDEO etc 
    Option          "TVStandard" "PAL-G" #or NTSC etc 
    Option          "ConnectedMonitor" "Monitor[1]" 
    BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection



Section "Screen"
    #Option         "AddARGBGLXVisuals"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "Coolbits" "1"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1080" "1280x720" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1080" "1280x720" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1080" "1280x720" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1080" "1280x720" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1080" "1280x720" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080" "1280x720" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Device         "Device[1]"
    Identifier     "Screen[1]"
    Monitor        "Monitor[1]"
    DefaultDepth   24
    SubSection     "Display"
        Depth      16
        Modes      "1920x1080_60"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

