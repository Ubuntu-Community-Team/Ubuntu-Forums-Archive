---
title: "Why are games (2d so laggy)?"
date: 2009-06-08
forum: Multimedia Software
---

### Post by xZachtmx on 2009-06-08
Ok... when i installed ubuntu i downloaded java for linux and played a java game.  I didnt install any atigraphics driver or anything it is just how it is.  BEcause when i tried to before... i had to renistall ubuntu.  i havent tried 3d games yet but any 2d game is a bit too laggy.  

here is my xorg.conf

Section "Files"
    RgbPath    "/usr/X11R6/lib/X11/rgb"
    FontPath    "/usr/share/fonts/misc/"
    FontPath    "/usr/share/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath    "/usr/share/fonts/75dpi/"
    FontPath    "/usr/share/fonts/100dpi/"

#    ModulePath    "/usr/X11R6/lib/modules"

EndSection

Section "Module"

# This loads the DBE extension module.
    Load        "glx"
    Load    "dbe"
    
    SubSection    "extmod"
    Option    "omit xfree86-dga"
    EndSubSection
   
    Load    "type1"
    Load    "freetype"

EndSection

Section "ServerFlags"

# Set the basic blanking screen saver timeout.

    Option    "blank time"    "10"    # 10 minutes

# Set the DPMS timeouts.  These are set here because they are global
# rather than screen-specific.  These settings alone don't enable DPMS.
# It is enabled per-screen (or per-monitor), and even then only when
# the driver supports it.

    Option    "standby time"    "20"
    Option    "suspend time"    "30"
    Option    "off time"    "60"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier    "Keyboard1"
    Driver    "kbd"

# Set the keyboard auto repeat parameters.  Not all platforms implement
# this.

    Option    "AutoRepeat"    "1000 50"

# These are the default XKB settings for xorg

    Option    "XkbModel"    "pc104"
    Option    "XkbLayout"    "us"
#    Option    "XkbVariant"    ""
#    Option    "XkbOptions"    ""

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier    "Mouse1"
    Driver    "mouse"

    Option    "Protocol"    "IMPS/2"
    Option      "ZAxisMapping"  "4 5"

EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

Section "Monitor"

    Identifier    "Generic Monitor"
    HorizSync    30 - 85
    VertRefresh    50 - 160
    Option    "dpms"

EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

Section "Device"
         Identifier     "Radeon"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"

EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier    "Screen 1"
    Device    "Radeon"
    Monitor    "Generic Monitor"
    DefaultDepth 24

    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" 
#        ViewPort    0 0
#        Virtual     800 600
    EndSubsection

    SubSection "Display"
    Depth        16
        Modes        "1280x1024" "1024x768" 
    EndSubSection

    SubSection "Display"
    Depth        8
        Modes        "1024x768" 
    EndSubSection

EndSection


# **********************************************************************
# ServerLayout sections.
# **********************************************************************


Section "ServerLayout"
    Identifier    "simple layout"
    Screen    "Screen 1"
    InputDevice    "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection



---------------------------------------------------------------------------------------------------------------

so... my graphics card is radeon x1300 Pro .  I am assuming this lag problem has to do with my graphics driver so i am relying on these forums to help me because i am used to the cataclyst control center but i only had the cd for windows.  I love linux but i need to know how to fix this problem.

---

