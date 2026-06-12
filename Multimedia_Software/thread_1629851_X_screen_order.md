---
title: "X screen order"
date: 2010-11-24
forum: Multimedia Software
---

### Post by JasonFWard on 2010-11-24
I submitted what I thought was a bug to Nvidia, in effect, I have 3 screens and 2 video adapters, and OpenGL only works on one of them.

The reply I got is as follows> This is the expected behavior:

[    20.992] (WW) NVIDIA(1): The GPU driving screen 1 is incompatible with the rest of the
[    20.992] (WW) NVIDIA(1):     GPUs composing the desktop.  OpenGL rendering will be
[    20.992] (WW) NVIDIA(1):     disabled on screen 1.
[...]
[    21.174] (WW) NVIDIA(2): The GPU driving screen 2 is incompatible with the rest of the
[    21.174] (WW) NVIDIA(2):     GPUs composing the desktop.  OpenGL rendering will be
[    21.174] (WW) NVIDIA(2):     disabled on screen 2.

This is documented in the README:
[ftp://download.nvidia.com/XFree86/Linux-x86/260.19.21/README/xineramaglx.html](ftp://download.nvidia.com/XFree86/Linux-x86/260.19.21/README/xineramaglx.html)

You can improve things by changing the order of the screens so that
screen 0 is on the GeForce 8400 GS, and then only the screen driven by
the GeForce 6150SE should be black.Now I've done a great deal of searching but I cannot even find a hint, let alone instructions on how to change the order of my screens.

Here's a [pastebin of my XCONF]("http://pastebin.com/CK2qrLAD") if someone can help me.

---

