---
title: "Restoring mesa drivers for ATI at Feisty"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by tmas on 2007-10-24
I have som problems after i tried to install fglrx_8.41.7 on my ati mobility 9000 card. I later found out that ati dont inlcude any support for such a old car, and therefor I`m trying to reinstall the original mesa configuration cause that seemed to work better than my current setup.

Now neither fglrxinfo or fgl_gears etc will work.
I also get som problems with some programs needing the libGL modules.

This is what happenings:

fglrxinfo:
Segmentation fault (core dumped)

Sometimes it say`s I`m missing libGL.so.1

So all I need to do is to reinstall the mesa driver as it was when I first installed Feisty.

What do do?

i need help on this one! :)

Thomas

---

### Post by aoanla on 2007-10-24
Erm.

fglrxinfo and fgl_gears are designed to work with the fglrx driver... I'd expect them not to work if you removed it. Or was that what you were trying to say?

---

### Post by tmas on 2007-10-24
when using fglrxinfo before I got the standard:

    $ fglrxinfo 
    display: :0.0 screen: 0 
    OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
    OpenGL renderer string: Mesa GLX Indirect 
    OpenGL version string: 1.2 (1.5 Mesa 6.4.1) 

Now it only shows:

Segmentation fault (core dumped)

Anyway, I would like to restore my original mesa drivers cause things worked better with those!
Howto?

Thomas

---

### Post by tmas on 2007-10-24
[SOLVED]

There was something wrong with the current libGL, so I needed to complete remove (not reinstall or something like that) and then install the libgl1-mesa-swx11 and then it seems to work!

thomas@laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 1.5 Mesa 6.5.2

---

