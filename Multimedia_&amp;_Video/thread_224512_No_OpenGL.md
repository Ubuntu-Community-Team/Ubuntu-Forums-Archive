---
title: "No OpenGL ??"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by originof on 2006-07-28
Hi to all
I use cedega for play with some games, but when i try the OpenGL Direct Rendering test it result negative...

> Your OpenGL drivers do not appear to be setup correctly. Please check the documentation for your Linux distribution and your graphics card drivers to ensure proper installation.


I have an ATI radeon 9600XT with fglrx driver

```
fglmanuel@ubuntu-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

manuel@ubuntu-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

Anyone can help me ??
How can i use OpenGL direct rendering ??

I'm italian, and my english suck...

---

### Post by originof on 2006-07-28
nothing ??:sad:

---

### Post by originof on 2006-07-28
in second page...up

---

### Post by originof on 2006-07-29
up

---

### Post by whatever on 2006-07-29
the output of fglrxinfo looks fine,
i'd say that the cedega test reports wrong results.

can you run **fgl_glxgears**? if this works your opengl acceleration is ok.

---

