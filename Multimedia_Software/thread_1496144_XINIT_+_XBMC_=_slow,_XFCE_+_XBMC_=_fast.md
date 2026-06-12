---
title: "XINIT + XBMC = slow, XFCE + XBMC = fast"
date: 2010-05-28
forum: Multimedia Software
---

### Post by karlbright on 2010-05-28
Hey people of the ubuntu,

Having some issues setting up XBMC on a minimal install, quick rundown of what ive done from a minimal server install to where the issue occured.

```

installed x-window-system
added xbmc repository
install python-software-properties pkg-config
install xbmc

```The box im running has the R350 Radeon 9800 pro as you can see from the lspci | grep VGA outpout
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
```The issue i am having is when i run xinit xbmc the framerate is horribly slow, the menus chug and i cant get anywhere with it.

Just for a test i installed a minimal xfce install, started it up with startx and ran xbmc from there, it runs fine.

From my understanding it would be an issue with my xorg.conf but after messing with that for awhile i still havent had any luck and now get segmentation faults when running glfxinfo. I am unable to use the FLGRX drivers as support for R350 series was cut in Feb 2009.

Is there something i have not yet looked up in regards to the differences between xinit and startx? I have tried creating a .xinitrc file with xbmc within it and still no luck. 

For reference here is my mangled xorg.conf:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
    Option "AccelMethod" "XAA"
    Option "AccelDFS"    "1"
    Option "AGPMode" "1"
    Option "AGPFastWrite" "0"
    Option "GARTSize" "64"
    Option "EnablePageFlip" "1"
    Option "ColorTiling" "1"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "DRI"
    Mode        0666
EndSection

Section "Module"
  Load "glx"
  Load "dri"
EndSection

```

Any assistance or fingers pointing me in the right direction would be greatly appreciated. Been hitting my head against the wall for a while now.

---

