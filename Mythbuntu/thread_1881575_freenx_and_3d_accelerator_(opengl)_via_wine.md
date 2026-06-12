---
title: "freenx and 3d accelerator (opengl) via wine"
date: 2011-11-15
forum: Mythbuntu
---

### Post by diskmaster23 on 2011-11-15
I have an lucid mythbuntu box with the main user david being used. I wanted to be able to use my machine remotely via freenx, but not the same screen that is being used on the TV. The problem is, awhile back I updated the box. Ever since I updated and when logging into freenx using david the frontend tries to load and keeps autoreloading when it crashes. As a result, I created a different user account, named bob, and all has worked out well. User bob does not have myth frontend trying to load, so problem solved.

Until I tried to run some 3D games via wine. It just doesn't work under freenx. It seems that opengl isn't loading. So, I thought, that by using virtualgl it would solve the problem. But it still isn't finding the opengl.

I've reinstalled new drivers, tried virtualgl, and turbovnc.

So...how do I get freenx, directx, and opengl to work together?

the error
```
00D2FBC0 00D2FBC4Xlib:  extension "NV-GLX" missing on display ":2008.0".
Xlib:  extension "NV-GLX" missing on display ":2008.0".
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly (using GL renderer "Mesa GLX Indirect", version "1.2 (1.5 Mesa 6.4.1)").
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
fixme:dpnet:IDirectPlay8PeerImpl_Close (0x131d28)->(0): stub

```

glxinfo | grep direct
```

Xlib:  extension "NV-GLX" missing on display ":2008.0".
Xlib:  extension "NV-GLX" missing on display ":2008.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

---

