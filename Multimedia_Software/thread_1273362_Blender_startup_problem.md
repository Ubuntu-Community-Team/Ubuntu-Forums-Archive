---
title: "Blender startup problem"
date: 2009-09-23
forum: Multimedia Software
---

### Post by jithu on 2009-09-23
I'm having a pretty strange problem with my ubuntu 9.04 and Blender.
When i try to launch blender from terminal, i get this error message:

```
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x9
  Serial number of failed request:  12
  Current serial number in output stream:  13
```I got this problem after an update.
I'm also unable to enable desktop effects.
Also when i try to watch a video in fullscreen, firefox quits automatically.

I've got a Nvidia Geforce 9400GT graphics card.
I hope someone can help me to solve this problem..

Thanks in advance!

---

### Post by jithu on 2009-09-25
is there someone who can help me?

---

### Post by genjix on 2009-09-25
$ glxinfo | grep "direct rendering"
direct rendering: Yes

if it says no, then your problem is lack of 3d

---

### Post by jithu on 2009-10-02
The problem is that GLX is missing.
Is there anyway to solve this problem? Better if i don't have to reinstall ubuntu.

I've NVIDIA accelerated graphics driver(version 180) enabled.

Thanks again.

---

