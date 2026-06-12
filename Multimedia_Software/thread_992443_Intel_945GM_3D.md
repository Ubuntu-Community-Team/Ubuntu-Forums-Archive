---
title: "Intel 945GM 3D"
date: 2008-11-24
forum: Multimedia Software
---

### Post by polymath on 2008-11-24
I have a acer aspire 3680 laptop with a intel 945GM video card.  I thought this was great, having read that 3D is enabled and autodetected by default on these cards since gutsy.  However, i installed TA:Spring on the computer and the map is all white.  The spring ubuntu install guide says this is the result of:
> 
**_Map is White_** 
If the whole map is only shades of white and grey, there is a problem with your display driver. Maybe your gpu is very old and does not support some needed opengl feature. For example I had this problem with matrox g550 but not with some very old geforce.


Can anyone help me figure out how to fix this? The same problem occurs on a dell dimension 2400 with an intel 82845G card.  This is also supposed to work in ubuntu.

BTW:  Am using intrepid normal (gnome) desktop release, but doesn't work with KDE either.

---

### Post by shanepardue on 2008-12-26
Try installing driconf with apt and enabling S3TC Texture Compression under the image quality tab.

---

