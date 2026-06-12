---
title: "Fresh Install - Wireless"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by Jerim on 2006-06-14
Okay, I asked a lot of questions about wireless but never got any answers. Finally, I did a clean install and am now sitting on top of a fresh install. (Mostly because I had been through so many tutorials, that I didn't remember everything I had done.)

Before I do anything, I am wondering if anyone one can point me toward THE go-to tutorial on setting up a Broadcom 4318 wireless chipset. I am running a Dell b130. 

Please keep in mind that my wireless card is listed as eth1 in the network settings panel. I tried activating it but nothing happened. Don't know if I need to remove that or not.

---

### Post by ????? on 2006-06-14
I also have a 4318. have you tried [This one](http://www.ubuntuforums.org/showthread.php?t=190177)? (it may bug on wep/wpa enabled networks

---

### Post by Jerim on 2006-06-16
Okay, that worked like a charm. The key is to use the bcmwl5a.inf file instead of the bcmwl5.inf file.

---

