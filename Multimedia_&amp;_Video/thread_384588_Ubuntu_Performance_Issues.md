---
title: "Ubuntu Performance Issues"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by balu123 on 2007-03-14
Hey,

I'm using Ubuntu for a couple of days now and I'm really satisfied besides of performence issues I noticed using for example Google Earth:

This is my computer:
P4 2,6 GhZ
1024 MB Ram
Ati Radeon x850 

I'm using the radeon driver, because I cannot get 3d accleration with fglrx.
And I really have problems to use google earth or websites like this [http://www.ubuntuusers.de/map]("http://www.ubuntuusers.de/map").
It becomes veeeeery slow then and it's impossible to go ahead with google earth or firefox/opera.

This is my output for 3D:

$ glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes 

Do you have any idea what to do?

Balu

---

### Post by balu123 on 2007-03-14
I get this when starting google earth:


nstalling desktop menu entries...
libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 412
Software fallback:ctx->Line.SmoothFlag
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 475
TODO - double side stencil !
***************************************************************************

---

### Post by balu123 on 2007-03-18
No idea anybody?

---

### Post by Dekunuts on 2007-03-18
maybe you should follow this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

to make sure your graphics card is working correctly

---

