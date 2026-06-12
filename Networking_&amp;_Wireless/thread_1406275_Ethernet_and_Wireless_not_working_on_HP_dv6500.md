---
title: "Ethernet and Wireless not working on HP dv6500"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by zazou0 on 2010-02-13
I just installed Ubuntu 9.10 on my HP dv6500, and neither the wireless won't work. I don't see any drivers under System >> Administration >> Hardware Drivers, and I can't connect it to the internet any other way when I'm running Ubuntu. (I still have Vista as a dual-boot, and it works fine there). Any advice? Thanks!


(Sorry about the title - the ethernet DOES actually work, but I can't seem to change the title of the post).

---

### Post by bkratz on 2010-02-13
Well the first thing to do is determine your wireless card.
Go to the terminal (Applications>>Accessories>>Terminal) and enter in

lspci | grep Wireless
(that is LSPCI in lowercase, W in uppercase)

and copy/paste the output back here.  If you don't see anything there just try 
lspci

---

