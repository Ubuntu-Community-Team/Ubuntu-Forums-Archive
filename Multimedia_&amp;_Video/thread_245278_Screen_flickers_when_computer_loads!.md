---
title: "Screen flickers when computer loads?!?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by brittney on 2006-08-27
Hi!

Ive just installed Ubuntu and everything works allright except that the screen flickers when the computer loads. it happens at any resolution and refreshrates i cant get rid of it! X uses i810 driver and it is an 21" monitor. dont know what kind of gfx card it is cause i just found the comp in a dusty old room =) its an old comp about 800mhz. in console mode alt-f1 and so on it works fine.. no flickering.. only in x.

Any ideas?

-bri

---

### Post by bcollignon on 2006-08-27
You have to change the refresh rate (in Hz) of your display driver.  This is done in the screen resolution area of Ubuntu along with resolution settings.  Check the specifications of your monitor.  The console won't flicker because it's a low-resolution text-based device.

---

### Post by brittney on 2006-08-28
well as i said it happens at all resolutions and refresh rates.. there is no problem with the resolutions and refreshrates.. its when the computer loads, cpu activity, ie loading a webpager, moving the mouse around alot.

-bri

---

### Post by brittney on 2006-08-28
*bump* please help me

---

### Post by Ziox on 2006-08-28
provide us with your Xorg.conf file:

cat /etc/X11/xorg.conf

---

