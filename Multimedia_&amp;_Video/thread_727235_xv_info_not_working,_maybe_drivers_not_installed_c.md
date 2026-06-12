---
title: "xv info not working, maybe drivers not installed correctly?"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by SyMpToM on 2008-03-17
Hi to all.

Being fed up with win, I decided to test my luck with Kubuntu.
I installed the alpha 6 of Kubuntu Hardy Heron 8.04.
Everything seems fine but I suspect that my xorg setup is not correct.

I'm using an ATi x1650 Pro with Kubuntu's proprietary drivers, I also managed to enable compiz...BUT:

When I try to watch a video in SMplayer, i can't select xv as the output method. It works only with X11 but this results to degraded performance and poor video playback.

My initial reaction was to run xvinfo but..

```
symptom@ubuntu:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```

As far as I can tell, direct rendering is enabled 

```

symptom@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
```

The framerates of fgl_glxgears
```

symptom@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
6529 frames in 5.0 seconds = 1305.800 FPS
8150 frames in 5.0 seconds = 1630.000 FPS
8073 frames in 5.0 seconds = 1614.600 FPS
```

The output of fglrxinfo

```
symptom@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7412 Release
```

The xorg.conf file
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us,el"
        Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
EndSection
```

and finally some lines from the Xorg0.log

```

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): could not detect X server version (query_status=-3)
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".

```

Despite my lack of experience, am I right to suspect an erroneous setup of the drivers?

---

### Post by lookoutmountainman on 2008-05-09
I found that this enabled XVideo
Section "Device"
        Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "TexturedVideo" "on"

EndSection

---

