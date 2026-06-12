---
title: "Messed up my nvidia/xorg/direct rendering"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by blakecraw on 2007-05-20
Well, earlier today I decided to install the nvidia-glx-new package, as I'm using an Nvidia Go 7600 card on my laptop and it is supposed to go with that driver, but after doing so something is not right. 

What I did was disable restricted drivers, install the nvidia-glx-new package, which removed the nvidia-glx package, and then I ran nvidia-xconfig-enable, which I read on some website (since then I have found out I should have just run nvidia-xconfig, please let me know if that's wrong also). After that, I tried to restart x, and ended up having to change the driver from nvidia to nv in my xorg.conf to start x at all. 

Now if I run glxinfo I get this in return:

$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

This is after removing nvidia-glx-new, re-enabling the restricted drivers, and reverting to my backed up xorg.conf 

Any help would be greatly appreciated, even if it just lets me revert to the nvidia-glx drivers, which I was able to get direct rendering with.

Blake

---

