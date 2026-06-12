---
title: "Ubuntu, dualhead2go and widescreens"
date: 2010-06-30
forum: Multimedia Software
---

### Post by Inaimathi on 2010-06-30
I'm trying to set up my dualhead2go (digital edition) to work with a pair of widescreen monitors. It sort of works out of the box, but the best resolution I can get is 2048x768 (which is already distorted. 2560x1024 would just be worse).

I've added the following modeline to xorg

"3360x1050_60.00"  293.75  3360 3576 3928 4496  1050 1053 1063 1089 -hsync +vsync

which I figured would do the trick. It kind of does; the resolution is set correctly, but it's squished to one monitor, and the whole point was to spread it across two. 

Can anyone help me resolve this?

---

