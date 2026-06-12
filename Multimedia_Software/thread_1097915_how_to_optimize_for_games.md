---
title: "how to optimize for games"
date: 2009-03-16
forum: Multimedia Software
---

### Post by urd on 2009-03-16
hi, i'm new with ubuntu and i want to optimize it for 3d games such as world of warcraft, after a lot of time i can run wow in ubuntu whit wine. and i just wondering if exist any way to optimize my laptop for playing, and obtain the best fps posible

i have a toshiba satellite laptop
2gb ram
ati mobility radeon x1200 (with the latest drivers for linux)
thurion x2 of 1.9 ghz procesor

i will apreciated any help

thanks

---

### Post by Neo_The_User on 2009-03-16
To enable hardware accelerated video on pre-R500 cards, edit /etc/X11/xorg.conf to include the following lines without [...]
File: /etc/X11/xorg.conf
```

Section "Device"

    [...]
    Driver "fglrx"
    Option "VideoOverlay" "on"
    Option "OpenGLOverlay" "off"
    [...]

EndSection

```

Note that when Visual Effects (Compiz) are active, flickering and artifacts may occur in OpenGL applications and hardware accelerated video windows (particularly with R300 chipset). To prevent this, disable Visual Effects.

On newer cards the options below enables Visual Effects and video to be played without flicker. The Textured video option can be turned on, but this can cause flicker or diagonal artifacts when playing videos.
File: /etc/X11/xorg.conf
```

Section "Device"

    [...]
    Driver "fglrx"
    Option "VideoOverlay" "off"
    Option "OpenGLOverlay" "on"
    Option "TexturedVideo" "off"
    [...]

EndSection

```

Be sure you don't install the drivers via hardware drivers. use --buildpkg.

Follow the guide here:

[http://ubuntuforums.org/showthread.php?t=1091804&page=2](http://ubuntuforums.org/showthread.php?t=1091804&page=2) 

My post is somewhere in there explaining everything on page 2.

---

### Post by urd on 2009-03-16
thanks, i'm going to try it!

---

### Post by Neo_The_User on 2009-03-16
> **urd said:**
> thanks, i'm going to try it!

no problem. good luck and take your time.

I'm assuming it worked.

---

