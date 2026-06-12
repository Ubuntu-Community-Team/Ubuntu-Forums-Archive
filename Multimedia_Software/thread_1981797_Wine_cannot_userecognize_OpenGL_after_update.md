---
title: "Wine cannot use/recognize OpenGL after update"
date: 2012-05-17
forum: Multimedia Software
---

### Post by Orpheon on 2012-05-17
I've used wine for a very long time, and one of the things I've used it for was for a small game made in game maker which I like very much.
Today, an update came through, wanting to update opengl. I accepted, and restarted the system as was required.
Wine is now incapable of running that game (Which is 2d, btw). I tried running it in the console, with this output:[URL="http://pastebin.com/ckAS7G7z"]http://pastebin.com/ckAS7G7z
[/URL] (The missing sound server is normal and on purpose. That is not the problem)
```
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D8 is not available without OpenGL.
```I first went to the IRC, here is what I got from there:[http://pastebin.com/uRd6q7G0](http://pastebin.com/uRd6q7G0)

OpenGL native works fine, my own programs in it had no problem running. I then found this: [http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)
and followed it, because for some reason I didn't have nvidia-current.

Didn't fix it.
So now I'm sort of stuck. Does anyone have any idea what could be doing this, and more importantly, how to fix it?


PS: I'm on a Ubuntu 12.04 64-bit, nvidia, wine version 1.4.

---

