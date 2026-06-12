---
title: "Black screen and hard reboot w/nvidia restricted drivers"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by Mander on 2008-04-17
I originally asked this in the wrong place, and I missed the similar threads.  I'm sorry.

Anyway, here is my version of this problem:

I'm running 7.04, installed using Wubi, on an Acer Aspire 7520 laptop with AMD Athlon 64 x2 dual-core processor, 1GB Ram, Nvidia GeForce 7000m, and a 17" widescreen display.  I had problems getting the newer versions to work, so I'm sticking with 7.04 for the moment.  

The screen resolution is too low and the whole screen looks fuzzy, and I'm having trouble getting a more appropriate resolution.  When I tried enabling the nvidia restricted drivers,  after the system rebooted, I got the Ubuntu splash screen and then nothing but a blank black screen.  Nothing was responsive except ctrl+alt+delete to hard reboot (alt+f1 didn't open a console, so I couldn't try to fix it from there).

I managed to roll back the xorg file to the Vesa drivers configuration that was working before, so I'm back to square one.  I'm not sure what to try next--I've seen [this thread]("http://ubuntuforums.org/showthread.php?t=410708&page=2") but I'm not really sure what that solution does, so I don't know if it is appropriate for me.

---

### Post by banished_one on 2008-04-17
have you installed the latest drivers of your video card ? if not you can do it easily via the program ENVY 

get it from : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

