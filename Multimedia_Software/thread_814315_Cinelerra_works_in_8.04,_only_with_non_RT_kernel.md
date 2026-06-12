---
title: "Cinelerra works in 8.04, only with non RT kernel?"
date: 2008-05-31
forum: Multimedia Software
---

### Post by ubundah001g on 2008-05-31
Cinelerra (from Cinelerra Community Center)
Ubuntu Studio 8.04

Cinelerra works in Ubuntu Studio 8.04 but only with the Non-RT kernel. If I use the RT kernel, which was the default install kernel, then I can open Cinelerra in User Mode, get a tip of the day, and four windows, but can not select any of the menu widgets. If I reboot and switch to the non-RT kernel, then I can run Cinelerra in User Mode fine. If I run Cinelerra as root, then it will run in the RT kernel. 

Does anyone know why? Also, I would like to use the RT kernel with Cinelerra. How can I do that in User Mode?

---

### Post by deflagmator on 2008-08-13
Hello,
For me the only solution to work as normal user (instead of root) is to install the rt kernel.

I have tried all the possibilities and this is the only that work. The other generic kernel hanged cinelerra. (also as root)

I use hardy 2.6.24-19-rt kernel amd64 with the akirad repo and cinelerra-k8 package. Sound perfect with pulseaudio.

Today 3 hours working perfect. :)

---

