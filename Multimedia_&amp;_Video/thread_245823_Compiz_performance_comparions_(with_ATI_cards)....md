---
title: "Compiz performance comparions (with ATI cards)..."
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by mwob on 2006-08-28
Hi,

I keep seeing really fast videos posted on you-tube etc. showing XGL effects running incredibly fast, and yet when I use XGL & Compiz, its not so fast :(

I wondered what everyone else was experiencing? I'm running an ATI 9550 Gfx card (so its bound to be slower being ATI!), and its reporting these speeds from "glxgears":

7651 frames in 5.0 seconds = 1530.091 FPS
7617 frames in 5.0 seconds = 1523.368 FPS
7587 frames in 5.0 seconds = 1517.383 FPS

"fgl_glxgears"  (which I've never heard of until I hit tab in the terminal window!) gives these results:

Using GLX_SGIX_pbuffer
1004 frames in 5.0 seconds = 200.800 FPS
1101 frames in 5.0 seconds = 220.200 FPS

They seem pretty crap to me - are other peoples experiences similar?

---

### Post by Melcar on 2006-08-28
I recently installed XGL on my laptop running a 200M chip with the newest ATI drivers.  In glxgears I get a wooping 125fps on average:razz: .  As for actual performance, it's no where near as fast as some of the videos I've seen, but still usable (suprisingly).  The only reason I don't uses it anymore is because I would always get screen curruption when a window would open (I blame the LCD on the notebook).

---

### Post by evil_elman on 2006-08-28
> **Melcar said:**
> I recently installed XGL on my laptop running a 200M chip with the newest ATI drivers.  In glxgears I get a wooping 125fps on average:razz: .  As for actual performance, it's no where near as fast as some of the videos I've seen, but still usable (suprisingly).  The only reason I don't uses it anymore is because I would always get screen curruption when a window would open (I blame the LCD on the notebook).

Same thing here (Mobility X600). I read somewhere about some sort of capping of the FPS on glxgears. This, of course, would make glxgears unusable as any kind of benchmark since the actual perfomance is much higher. 

Running Warsow for example is not a problem with regards to FPS for me.

---

### Post by mwob on 2006-08-29
OK, well I guess glxgears is only of limited use.

Maybe one day a good driver will come out for ATI cards....one day!

---

### Post by Melcar on 2006-08-29
Just did another run and this is what I get:

crapbox@ToGo:~$ glxgears -info
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
GL_RENDERER   = RADEON XPRESS Series Generic
GL_VERSION    = 1.2 (2.0.6011 (8.28.8))
GL_VENDOR     = ATI Technologies Inc.
GL_EXTENSIONS = GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
3828 frames in 5.1 seconds = 756.149 FPS
4271 frames in 5.0 seconds = 854.200 FPS
4263 frames in 5.1 seconds = 834.298 FPS
4267 frames in 5.1 seconds = 844.653 FPS
4267 frames in 5.0 seconds = 845.831 FPS
4141 frames in 5.0 seconds = 824.723 FPS
4267 frames in 5.1 seconds = 841.579 FPS
4249 frames in 5.0 seconds = 849.162 FPS
4267 frames in 5.0 seconds = 846.426 FPS
4267 frames in 5.0 seconds = 845.567 FPS
X connection to :1.0 broken (explicit kill or server shutdown).

This is with a 200M and the 8.28.8 drivers

---

### Post by killabc on 2006-08-29
My benchmark with ati 9600 xt + ati driver 8.28.8

glxgears -info
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
GL_RENDERER   = RADEON 9600 XT Generic
GL_VERSION    = 1.2 (2.0.6011 (8.28.8))
GL_VENDOR     = ATI Technologies Inc.
GL_EXTENSIONS = GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 
17045 frames in 5.0 seconds = 3408.956 FPS
24359 frames in 5.0 seconds = 4871.646 FPS
24294 frames in 5.0 seconds = 4858.699 FPS
24384 frames in 5.0 seconds = 4876.670 FPS
24339 frames in 5.0 seconds = 4867.766 FPS
24321 frames in 5.0 seconds = 4864.176 FPS
24321 frames in 5.0 seconds = 4863.260 FPS
24342 frames in 5.0 seconds = 4868.344 FPS
24320 frames in 5.0 seconds = 4863.940 FPS

---

