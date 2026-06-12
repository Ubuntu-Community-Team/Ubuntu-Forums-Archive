---
title: "Strance scores with glxgear"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by didobuntu on 2006-10-27
Hello,

Since I upgraded to Edgy (with many many unsolved problems) I noticed a strange score with glxgears. I own a laptop with an ATI X1600 Mobility radeon (256Mb for nothing !!).

My direct rendering is ok and fglrxinfo gives me:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

When I launch glxgears -printfs, I have the following scores:

glxgears -printfps
1248 frames in 5.0 seconds = 249.485 FPS
1250 frames in 5.0 seconds = 249.959 FPS
1250 frames in 5.0 seconds = 249.808 FPS
1250 frames in 5.0 seconds = 249.808 FPS
1239 frames in 5.0 seconds = 247.610 FPS
1250 frames in 5.0 seconds = 249.808 FPS

:confused:  with my old mobility radeon 7500 I have 610 FPS

And with the command fgl_glxgears I obtain the following:

fgl_glxgears
Using GLX_SGIX_pbuffer
3704 frames in 5.0 seconds = 740.800 FPS
3852 frames in 5.0 seconds = 770.400 FPS
3890 frames in 5.0 seconds = 778.000 FPS
3868 frames in 5.0 seconds = 773.600 FPS
3884 frames in 5.0 seconds = 776.800 FPS
3884 frames in 5.0 seconds = 776.800 FPS
3883 frames in 5.0 seconds = 776.600 FPS
3866 frames in 5.0 seconds = 773.200 FPS

So the scores with 3D are higher than with glxgears !!!

Normally I have to obtain scores around 4500 FPS with glxgears as it used to be under Drapper.

Any Idea ?

---

