---
title: "[SOLVED] Trident Cyberblade 3D video problems"
date: 2008-09-28
forum: Multimedia Software
---

### Post by dan5150 on 2008-09-28
Hey guys, 

I have used Windows for many years now, and have just taken the plunge into the Linux world.

Since I am not at all familiar with the Linux OS or commands I feel like a total Noob... 

I installed the latest version of Ubuntu last week on my old laptop, a Compaq Presario 12XL505. It has a Trident Cyberblade 3D inegrated video chipset. 

I had to choose the install option that was the "safe mode" video version, (sorry I can't remember exactly what it was called) since if I sleected the default install option, I would just get a blank screen.

Anyway, the OS is installed and seems to working correctly now, however the screen resolution and color depth don't appear to be as deep as they could be. 

I did a google search and found the following link:

[http://www.fixya.com/support/t113668-mandrake_7_1_compaq_presario_12xl222](http://www.fixya.com/support/t113668-mandrake_7_1_compaq_presario_12xl222)

However, it looks like I don't have an XF86Config
file in my /etc/ directory. 

Any help or suggestions would be greatly appreciated!

Thanks, 

-Dan-

---

### Post by overdrank on 2008-09-28
Hi and welcome, you may try and use the alt, F2 keys and enter this command 
```
gksu displayconfig-gtk
``` and setup your graphics and resolution there.

---

### Post by dan5150 on 2008-09-29
Thanks! This did the trick!

-Dan-

---

