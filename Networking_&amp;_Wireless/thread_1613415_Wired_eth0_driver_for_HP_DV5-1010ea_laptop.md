---
title: "Wired eth0 driver for HP DV5-1010ea laptop"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by gallowslad on 2010-11-04
Hi there
 
I'm fairly new to ubuntu and have been very impressed with the installation, ease of use, and most of all the fact that it works with my laptop's wireless, media buttons, and graphics without any problems. However I cannot find a driver for the eth0 wired connection which I need to use at work.
 
Anyone able to give me a hint at finding one? I am sure it doesn't work already.
 
Thanks

---

### Post by chili555 on 2010-11-04
Please open Applications > Accessories > Terminal and do:```
lspci -nn
```Feel free to strip away everything that's clearly not your wired ethernet card. Post it here and we'll proceed.> I am sure it doesn't work already.I am not sure.

---

### Post by P4man on 2010-11-04
Im not so sure either. Have you tried the wired network at home or at work? I strongly suspect its a configuration issue at work, but Ill await your response to the above post.

---

