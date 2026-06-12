---
title: "ATI 780g video playback flickering black"
date: 2008-09-28
forum: Multimedia Software
---

### Post by aaronpau on 2008-09-28
I recently installed Ubuntu on my PC and am having problems with black areas being drawn continuously (flickering) over the playing video. I have tweaked various xorg.conf changes, trying to fix it - no go. This happens even on very simple mpeg videos. Suggestions?

- Running in full screen does not exhibit this problem
- Turning vsync on/off just changes whether part or all of the screen goes black when it flickers.
- Tried both Totem (default) and VLC players - same result

Snip from fglrx section of xorg.conf:
```
Option "TexturedVideo" "on"
Option "TexturedVideoSync" "off"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
```

lspci -- 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
glxinfo:
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 2.1.7412 Release

Ubuntu 8.04.1
ASUS M3A78-EM
Radeon HD 3200 onboard video
fglrx ATI driver

---

### Post by aaronpau on 2008-09-30
It looks like ATI video acceleration for xvideo is completely broken. I had to disable hardware acceleration. This was easily done through the gstreamer-properties video tab. Once I set the output plugin to "No Xv" (no x-video), video playback worked without flickering. Unfortunately, this means that my CPU is working a lot harder than it should have to. I believe it also means that all other apps (like games, etc) that could try to use hardware acceleration cannot do so.

I saw comments that DRI 2 (Direct Rendering Interface version 2) is able to address this issue. Is this true? If so, is this going to be available to Ubuntu 8 users, or will I have to install it separately?

P.S. With all of these problems, should I go back to the open driver? The main reason I originally moved to it was to support my odd display resolution. Perhaps I can overcome this with the open driver and a bit of tweaking.

---

### Post by bufsabre666 on 2008-09-30
my 3850 did that too, if youre using the proprietary driver just add this to the end of the file:

```
Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

and add this under the server layout section:

```
        Option          "AIGLX"         "true"
```

---

### Post by LucidLoon on 2008-09-30
I have an ATI on my board and Flightgear and Google Earth were both flickering badly. I got the idea from a post about Google Earth flickering to go into appearance and turn off visual effects. I saw a dramatic improvement. Flightgear is now playable and Google Earth has no problems. I read there seems to be some sort of conflict between the ATI cards and Compiz-Fusion that messes things up. Don't know if this applies to your situation but it might be worth considering.

---

### Post by aaronpau on 2008-10-03
Thanks a million Lucid. I had been slapping myself for going with ATI, but turning off the Visual Effects to None inside my Appearance fixed the problem. Yay!

Does anyone know if this will be fixed soon?

---

### Post by binbash on 2008-10-03
set the output to X11 at your video player.It will be fixed %99 with compiz enabled.

---

