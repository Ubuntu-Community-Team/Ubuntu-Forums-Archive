---
title: "How to get Mesa3d working ?"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by B0rsuk on 2006-10-18
Hey

I've spent a lot of time trying to find a decent howto, especially ubuntu-ish.
In short, my Geforce2 MX 400 is very old, and it's basically broken. Once it gets hot, it freezes my machine.

**I'm trying to use Mesa3d instead - software acceleration. **
All I need is to get my glxgears working. At the moment:
```

b0rsuk@dziupla:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

I used to use 'nvidia' driver, but now use 'nv' because it doesn't freeze. Ubuntu 6.06 install/livecd successfuly runs 'vesa' or 'nv' drivers with mesa3d working (glxgears works), but I can't reproduce it, even when I analyze xorg.conf and so on.
Parts of my present xorg.conf :
```

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
(...)

Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nv"
        BusID           "PCI:2:0:0"


```

I still have nvidia-glx-legacy installed, but use 'nv' instead of 'nvidia'. Do I need to install any additional mesa packages ? I seem to have some already installed, and couldn't spot anything important missing.

Please help. I'd hate to buy a new card just to get Dominions3 demo working.

---

### Post by kvonb on 2006-10-18
Why not put an old power supply fan next to the video card to keep it cool, then use the nvidia driver?  I did the same with my old mx400, it worked well.

Regards,

Kev :)

---

### Post by B0rsuk on 2006-10-19
> **kvonb said:**
> Why not put an old power supply fan next to the video card to keep it cool, then use the nvidia driver?  I did the same with my old mx400, it worked well.


Because it may eventually break permanently. And it already seems to work worse now. Previously, it used to work once in a while and cooling it down used to help. It's much colder here now (winter's coming), and it freezes right away on first try. I needed install/livecd just to change my xorg.conf back to *nv*.

Even if setting up additional cooler would help, it would be riding the tiger. Asking for trouble. Besides, the 6.06 install cd clearly shows it IS possible to use mesa3d and glxgears, I just can't seem to reproduce it.

---

