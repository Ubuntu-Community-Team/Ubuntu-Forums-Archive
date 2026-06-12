---
title: "3D acceleration with NVIDIA legacy drivers"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Bezvardis on 2007-04-30
I have an NVIDIA RIVA TNT2 video card. Seems that I have installed the legacy driver OK and have changed "nv" to "nvidia" as it should be. But still there seems not to be any 3D support (e.g. 3D screensavers don't work) So my question is - does anybody know what should I do?

This is in Feisty. The drivers worked nicely under the previous version

Thanks in advance!

---

### Post by madmetal on 2007-04-30
open a terminal and give
glxinfo | grep direct

if the answer is yes then you are ok with 3D acceleration..
if not then you go drivers problem..maybe give a try to nvidia driver (not the legacy one)

---

### Post by Bezvardis on 2007-04-30
That gives me output like this

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
```

What does that mean? I have tried also the non-legacy drivers with no good result

---

