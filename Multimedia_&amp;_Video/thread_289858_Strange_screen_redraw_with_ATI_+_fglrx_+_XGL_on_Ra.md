---
title: "Strange screen redraw with ATI + fglrx + XGL on Radeon Mobility M300/X300 [video]"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by shadfc on 2006-10-31
Hey guys, I've been trying to get beryl or compiz working for a while now and I cant seem to get my ATI drivers working properly.  I'm using the newest ATI driver 8.29.6 which works fine in regular Xorg. 

```
# fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.6065 (8.29.6)
```
```

# glxinfo |grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY RADEON X300 Generic
```


Additionally, I can get into an XGL session with the script

```
# cat /usr/bin/startxgl.sh
#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
exec gnome-session
```


XGL starts fine and goes to the standard metacity Ubuntu desktop.  However, whenever I open a new application through the GUI, I get this strange screen redraw where it sections off the screen in black triangles that eventually cover the entire screen.  Then it redraws the whole screen in two big trianges.  See for yourself here [http://www.youtube.com/watch?v=sa2kIlQ7BA8]("http://www.youtube.com/watch?v=sa2kIlQ7BA8")

Here is the fglrxinfo output when run from the XGL session

```
# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.6065 (8.29.6)
```


When I try starting beryl from this messed up XGL, I get an error about the missing extension for texture from pixmap or something like that. 

Last, here are the relevant sections from my xorg.conf
```

Section "Module"
  Load  "i2c"
  Load  "bitmap"
  Load  "ddc"
  Load  "dri"
  Load  "extmod"
  Load  "freetype"
  Load  "glx"
  Load  "int10"
  Load  "type1"
  Load  "vbe"
EndSection

Section "ServerFlags"
   Option  "AIGLX" "off"
EndSection

Section "Extensions"
  Option "Composite" "Disable"
EndSection
Section "Device"
  Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
  Driver  "fglrx"
  BusID   "PCI:1:0:0"

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "no_accel" "no"
Option "no_dri" "no"
Option "DynamicClocks" "on"
Option "mtrr" "on"
Option "DesktopSetup" "Single"
Option "ScreenOverlap" "0"
Option "Capabilities" "0x00000000"
Option "CapabilitiesEx" "0x00000000"
Option "CenterMode" "off"
Option "PseudoColorVisuals" "off"
   Option  "Stereo" "off"
   Option  "StereoSyncEnable" "1"
   Option  "FSAAEnable" "no"
   Option  "FSAAScale" "1"
   Option  "FSAADisableGamma" "no"
   Option  "FSAACustomizeMSPos" "no"
   Option  "FSAAMSPosX0" "0.000000"
   Option  "FSAAMSPosY0" "0.000000"
   Option  "FSAAMSPosX1" "0.000000"
   Option  "FSAAMSPosY1" "0.000000"
   Option  "FSAAMSPosX2" "0.000000"
   Option  "FSAAMSPosY2" "0.000000"
   Option  "FSAAMSPosX3" "0.000000"
   Option  "FSAAMSPosY3" "0.000000"
   Option  "FSAAMSPosX4" "0.000000"
   Option  "FSAAMSPosY4" "0.000000"
   Option  "FSAAMSPosX5" "0.000000"
   Option  "FSAAMSPosY5" "0.000000"
   Option  "UseFastTLS" "0"
   Option  "BlockSignalsOnLock" "on"
   Option  "UseInternalAGPGART" "no"
   Option  "ForceGenericCPU" "no"
   Option  "KernelModuleParm" "agplock=0"
   Option  "PowerState" "1"
   Option  "RenderAccel" "False"

   Option  "backingstore" "true"
   Option  "AllowGLXWithComposite" "true" 

EndSection
```

I'd appreciate any help,
Jay

---

### Post by Merkidemis on 2006-11-01
I am getting this too, though not nearly as bad.  I can still see it redrawing the screen in triangles.  Dapper was working great, and this appeared after I did a dist-update to Edgy.  

I am running on a Compaq V2000 laptop with a Turion M-32 with an X200 Mobility.

---

### Post by underwater on 2007-03-07
I'm having horrible XGL problems now.  I have exactly this hardware, x300 fglrx drivers, etc.

---

