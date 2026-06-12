---
title: "XGL Session dont work Direct Rendereing"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by fabianoheringer on 2007-05-18
Hey Guys,

I am having the follow trouble here, I have an X800XT Platinum Edition and I get installed successfull , when a try the default gnome session the Direct Rendering works fine, but when i try to start a XGL Session (to use with beryl) i get no Rendering...

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
name of display: :1.0
display: :1  screen: 0
direct rendering: No
OpenGL renderer string: RADEON X800 XT Platinum Edition

Heres is my script to start XGL Session

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session

I have Ubunut Edgy 6.10


Anybody have some sugestions?

---

### Post by Steveway on 2007-05-18
This behaviour is correct.
Don't worry.

---

