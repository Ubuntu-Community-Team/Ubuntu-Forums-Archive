---
title: "nvidia drivers won't load"
date: 2008-08-24
forum: Multimedia Software
---

### Post by zeek0us on 2008-08-24
I'm new to linux after years in XP, and am getting into the joys of a more DIY OS.  My problem concerns the KWIN/Compiz window managers and NVidia drivers.

When I first installed kubuntu 8.04, everything went fine and I was asked if I wanted to use proprietary NVidia drivers, which I did.  Then I was trying to figure out how to get some of the cool desktop effects, so I downloaded compiz and got that work.  Only I don't really like how Compiz handles multiple desktops (same background on each is lame), so I went back to kwin.  Then I realized that I couldn't run any of the "GL" screensavers that were offered, so I went searching for all the drivers and such to pull that off.

Anyway, the problem started when I downloaded and installed Nividia's config package.  At this point, compiz was still installed but apparently not my active window manager.  Everything seemed to work with the Nvidia driver, but then I did a restart and got the "Low Graphics Mode" window and ended up having to run a recovery start which got everything working (with compiz active, strangely enough).

Now I simply cannot seem to get the Nvidia driver to load.  I get the nvidia splash screen before the kdm login window, then after I  log in I get a plain white screen -- it seems like kdm is loading, but with no video.  When I changed the driver in xorg.conf to "nv" instead of "nvidia", everything works again, only apparently without any OpenGL functionality.

Here's my xorg.conf, with the working settings shown and the killer one commented out:
  
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics Touchpad"
    Option	   "SHMConfig"	"true"
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

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option	   "SHMConfig"	     "true"
    Option	   "TapButton1"	     "0"
    Option	   "TapButton2"	     "0"
EndSection	

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
#    Driver         "nvidia"
    Driver	    "nv"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

