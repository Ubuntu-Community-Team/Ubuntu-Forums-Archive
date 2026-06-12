---
title: "Open source radeon driver : fictitious acceleration ?"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by zeProphet on 2007-07-11
Hi all,
I was wondering whether the open source radeon driver really provide 3D acceleration...

Here is the config I have :
- radeon 9200 agp (rv280) graphic card
- multiboot :
Windows 2000 with proprietary drivers and
Ubuntu Feisty with open source radeon driver, Xorg 7.2, kernel 2.6.20-16.
- xorg.conf file correctly configurated, I think (I am not a Linux beginner)
- direct rendering : yes
- never installed fglrx
- glxinfo | grep vendor -> SGI
- theoretically, open source radeon driver provide 3D acceleration for my graphic card.


I also have a small OpenGL program (written with glut), very simple, nothing complicated, that can be compiled both on Windows and Linux, no specific code, and that allows us to retrieve some FPS.

Test number 1 : I launch my small program on Windows, I get about 600 FPS, and a CPU usage about 3% while the 3D program is working.

Test number 2 : I launch my small program on Linux, I get about 400 FPS, and a CPU usage about 95% while the 3D program is working.


What I deduce ;
from test 1 : 3D acceleration is active on Windows.
from test 2 : there's no 3D acceleration with open source radeon driver.

I have tested many options in my xorg.conf, trying to have this alleged 3D acceleration working...

What do you think about that ? Do you want my device section from xorg.conf ? Anything else ?
Pleaaaase... Help... as Leeloo would say

David

---

### Post by zeProphet on 2007-07-11
up ):P

---

### Post by zeProphet on 2007-07-12
Nobody could tell me whether this false 3D acceleration provided by the open source radeon driver is normal or not ?

---

### Post by Baarhisveiki on 2007-07-12
Did u configure your drivers manually or did u try tru system/administration/restricted drivers manager?
There u should find ati radeon drivers. Click it. It worked for me.
Ati and linux dont work to well that is known. But before i went tru the above mentioned "procedure" instead of tru the hassel of line after line (there is a good tutorial on this forum-if only i remember where?:)) But that cant be too hard tru the search.

I rebooted and here u go...i had google earth installed before that and it didnt worked. New it spins like there is no tomorrow. 

Hope this works for u aswell.

---

### Post by zeProphet on 2007-07-12
Ok, I'll look into that.
But... I cannot use the proprietary fglrx ATI driver since my radeon 9200 is too old to be supported by recent fglrx drivers. So, I don't think that using the restricted driver manager will work, simply because the open source radeon driver is not restricted.
I'll try it anyway.
Thanks

---

