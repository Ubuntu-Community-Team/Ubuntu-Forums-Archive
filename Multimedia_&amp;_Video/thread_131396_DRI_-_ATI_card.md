---
title: "DRI - ATI card"
date: 2006-02-16
forum: Multimedia &amp; Video
---

### Post by guerra on 2006-02-16
Hail all!

I know there are many posts about this subject but i didnt manage to fix it after all that reading.

I have an ATI Radeon 9600 xt 128mb and i installed the fglrx driver via easyUbuntu. When i tried to play the nwn linux-native client it says: Failed to initialize graphics. I will show you teh output of some commands that mightb e useful. ( i use xorg )

[COLOR="Red"]fglrxinfo[/COLOR]
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

[COLOR="Red"]lspci[/COLOR] show my video card:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

[COLOR="Red"]glxinfo | grep "direct rendering"[/COLOR]
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

Obviously the problem is at the dri, direct rendering stuff, but i have no clue of how to fix it.

Any help is welcome!

Many thanks in advance!

Guerra

---

