---
title: "ATI Driver: 3D Ok, Xgl/Compiz Ok, FPS Ok - DRI NOT OK! glxinfo NOT OK!"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by bbmiojo on 2006-08-27
Ok, I have a strange situation over here.

I have installed the last ATI driver 8.28.8 and everything is working fine.
My Xgl/Compiz setup runs like a charm.
Glxgears prints nice FPS.
Fglrxinfo displays that it is using the correct driver, not mesa.
But, here is what is going on:

> miojo@nissim:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
16675 frames in 5.0 seconds = 3334.150 FPS
18264 frames in 5.0 seconds = 3635.413 FPS
18582 frames in 5.0 seconds = 3707.569 FPS

> miojo@nissim:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))

> miojo@nissim:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

> miojo@nissim:~$ cat /etc/X11/xorg.conf | grep dri
        Load  "dri"
        Option      "no_dri" "no"

So please someone answer me:
1) How to fix the "DRI missing" warning? How do I know if DRI is really working and so I should ignore this message?
2) Why glxinfo tells me that Direct Rendering is NOT working, but Xgl/Compiz runs fine!?

Thank you all!

---

### Post by IoCaster on 2006-08-27
I've got similar types of inconsistencie. My box has an nvidia card though.

> :~$ glxinfo | grep rendering
direct rendering: No

> :~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: NVIDIA Corporation

> :~$ glxgears
71521 frames in 5.0 seconds = 14285.043 FPS
76100 frames in 5.0 seconds = 15219.997 FPS
69769 frames in 5.0 seconds = 13942.739 FPS
68937 frames in 5.0 seconds = 13770.233 FPS
71431 frames in 5.0 seconds = 14286.187 FPS

The nvidia logo splashes up very nicely and xgl+compiz are functioning. At this point I'm inclined to let sleeping dogs lay, but there's definitely something weird going on here. It's really strange that it's not isolated to one particular graphics vendor.

---

### Post by bbmiojo on 2006-08-28
Anybody else with this problem? :D

:rolleyes:

---

### Post by Ziox on 2006-08-28
I believe that the "problem" is caused by XGL...it's very complicated, but I think if you turn XGL of, then glxinfo will give direct rendering : Yes...

---

### Post by bbmiojo on 2006-08-28
> **Ziox said:**
> ... I think if you turn XGL of, then glxinfo will give direct rendering : Yes...

Even so, why the hell I'm getting these "DRI missing" warnings?!

---

### Post by Ziox on 2006-08-28
> **bbmiojo said:**
> Even so, why the hell I'm getting these "DRI missing" warnings?!

my bad, and please don't swear here....and that's what I meant....DRI missing is from the layer 0, and I believe that XGL uses DRI of layer 1, which makes Ubuntu/Xorg give a false positive....if that makes sense...I'm not a expert on this, I just read it somewhere...

---

### Post by bbmiojo on 2006-08-29
> my bad, and please don't swear here....and that's what I meant....DRI missing is from the layer 0, and I believe that XGL uses DRI of layer 1, which makes Ubuntu/Xorg give a false positive....if that makes sense...I'm not a expert on this, I just read it somewhere...

I didn't want to be rude, sorry... :) My bad too

What kind of layer are you talking about? And where did you read about this issue?

---

