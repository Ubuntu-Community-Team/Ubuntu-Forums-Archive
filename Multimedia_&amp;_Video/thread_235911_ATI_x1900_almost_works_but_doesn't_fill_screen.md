---
title: "ATI x1900 almost works but doesn't fill screen"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by jkbrennan77 on 2006-08-13
I'm trying to get an ATI AIW X1900 to work with a Syntax LT37HVS LCD ([http://secure.syntaxgroups.com/products/detail.jsp?pid=LT37HVS](http://secure.syntaxgroups.com/products/detail.jsp?pid=LT37HVS)) on Ubuntu 6.06.1.  I can get the video to work at various resolutions and get ~9000 fps with glxgears.  The problem is that I can't get the desktop to fill the entire screen i.e., there is a black band around all the edges.  Iff I change the resolution to 1920x1080 (in xorg.conf) then it uses the full screen, but the desktop is larger than the screen i.e., I'm missing content from around all the edges.

I can use an MSI K8NGM2-FID based on Nvidia 6150 chipset and it fills up the screen at 1280x720 resolution with this modeline: 
```
ModeLine       "1280x720_60.00" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
```
Using this modeline (full xorg.conf below) with the X1900 ends up with resolution at 1152x648x60.  I can change the resolution using "screen-resolution" within gnome.  If I change it to 1920x1080x30 I end up with the desktop being cut off around the edges.

I'm using:
linux-restricted-modules-2.6.15-26-amd64-k8   2.6.15.11-3 
xorg-driver-fglrx   7.0.0-8.25.18+2.6.15.11-3
fglrx-control   8.25.18+2.6.15.11-3
```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection
Section "Files"
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
Section "Module"
        Load  "bitmap"
        Load  "dbe"
        Load  "ddc"
        Load  "GLcore"
        Load  "glx"
        Load  "dri"
        SubSection "extmod"
                Option      "omit XVideo"
                Option      "omit XVideo-MotionCompensation"
                Option      "omit XFree86-VidModeExtension"
        EndSubSection
        Load  "freetype"
        Load  "int10"
        Load  "type1"
        Load  "v4l"
        Load  "vbe"
EndSection
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection
Section "Monitor"
        Identifier   "DFP-0"
        HorizSync    15.0 - 46.0
        VertRefresh  59.0 - 61.0
        ModeLine     "1280x720_60.46" 75.0 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
        Option      "DPMS"
EndSection
Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:4:0:0"
EndSection
Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "DFP-0"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1280x720"
        EndSubSection
EndSection
Section "DRI"
        Mode         0666
EndSection
```

The associated Xorg.log.0 is at:
[http://home.nc.rr.com/jhjb/Xorg.log.0](http://home.nc.rr.com/jhjb/Xorg.log.0)

---

