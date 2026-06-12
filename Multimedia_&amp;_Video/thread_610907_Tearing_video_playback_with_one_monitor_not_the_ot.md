---
title: "Tearing video playback with one monitor not the other"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by boast on 2007-11-12
When playing videos, I get choppy tearing video on my LCD (1680x1050 @ 59.88Hz), but on my CRT (800x600 @ 85.14Hz) the videos play smoothly. 

I have all the vblank stuff checked on nvidia-settings and for compiz. My video card is an FX5500. 

For compiz settings, I unchecked detect refresh rates, and I manually put in 60Hz. 

:(

---

### Post by JasonF on 2007-11-12
You won't be able to sync to both monitors. The nvidia-settings program should let you choose which you want to sync to, but it won't be both.

---

### Post by boast on 2007-11-12
> **JasonF said:**
> You won't be able to sync to both monitors. The nvidia-settings program should let you choose which you want to sync to, but it won't be both.

it always seems to pick the rate of the CRT. How do I make it pick the LCD one? If I put both to 60Hz, the LCD still gets dropped to 40Hz in full screen.

---

### Post by JasonF on 2007-11-12
nvidia-settings should let you choose which display to sync to for XVideo (right under the box to actually enable vsync).

For OpenGL output, [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-e.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-e.html) describes an environment variable you can set to choose which display to use

---

