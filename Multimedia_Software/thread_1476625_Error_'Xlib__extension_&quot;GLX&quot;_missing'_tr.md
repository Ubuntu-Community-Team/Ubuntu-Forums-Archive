---
title: "Error 'Xlib:  extension &quot;GLX&quot; missing' trying to run 3D game with NVidia graphic card"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Nybb on 2010-05-08
I think this is the right forum to post this in...So, I'm trying to see if I can run StarCraft 2 on my laptop. I've managed to successfully install it and patch it, but running it via Wine in the terminal gives this:

```
Xlib:  extension "GLX" missing on display ":1.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

```


I'm using Ubuntu 10.04 with an NVidia on-board graphics card, using the recommended proprietary driver. Not sure what other information I should give. Any ideas are greatly appreciated.

---

### Post by lidex on 2010-05-08
What are the output of these commands:
```
LIBGL_DEBUG=verbose glxinfo | head
cat LIBGL_DEBUG=verbose glxinfo | grep error
glxinfo
grep -n "^(EE)" /var/log/Xorg*log
```
In a terminal="Applications->Accessories->Terminal"
Please use code tags.

---

