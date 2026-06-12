---
title: "Nvidia no opengl"
date: 2005-12-29
forum: Multimedia &amp; Video
---

### Post by sleepkreep on 2005-12-29
I've been fighting with this for a while and am at a loss.  I installed the nvidia-glx package.  Composite extension runs very smooth since I added 
Option "RenderAccel" "on"
to my device section.  So that at least is being accelerated.  But when I run glxgears, I get:

$glxgears
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.

My Xorg.0.log file shows:

(EE) GLX is not supported with the Composite extension
(WW) NVIDIA(0): Option "EnablePageFlip" is not used
(==) RandR enabled
Symbol __glXgetActiveScreen from  module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!


But this can't be right can it?  What good is having composite transparency if you can't use opengl?  I read not to load dri but glx instead.  Here are my interesting sections from xorg.conf file:

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section  "Device
        Identifier      "Nvidia GeForce FX 5500"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "NoLogo" "on"
        Option "CursorShadow" "false"
        Option "CursorShadowAlpha"      "10"
        Option "CursorShadowXOffset"    "2"
        Option "CursorShadowYOffset"    "2"
        Option "RenderAccel" "true"
        Option "EnablePageFlip" "true"
        Option "Overlay" "1"
        Option "AllowGLXWithComposite" "Off"
        Option "Accel" "on"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "enable"
EndSection

---

