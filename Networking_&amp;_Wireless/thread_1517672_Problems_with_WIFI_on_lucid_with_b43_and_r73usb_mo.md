---
title: "Problems with WIFI on lucid with b43 and r73usb modules"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by eddxpt on 2010-06-25
Hi,

Since ubuntu 9.04 (64bits) that i have troubles with my wifi network connection.
I am now using Lucid 64 bits (up to date in everything).

I can basically connect to every type of network, but my link is inconsistent, having some periods where the connection is on but i can't ping my router. 

If i type "route" in the bash when i can't reach the internet it takes a while until i can see my kernel routing table.

I have two wireless cards (b43 kernel module and r73usb).

Experimented with both and the problem is the same.

I have used NetworkManager, WiCd, manual configuration. And the problem persists.

At first i thought my router was the problem but after using 3 types of firmwares and experimenting with windows i noticed that the problem was in my ubuntu box.

This setup was working fine with ubuntu 8.04.

Right now i'm at work and i cannot follow the instructions to properly post this issue. I will follow up the thread with the details of my configuration.

Any help with this would be very useful.

---

### Post by eddxpt on 2010-06-26
Hi again,

So i managed to solve the issue by upgrading the kernel to version 2.6.34-020634-generic.

With kernel 2.6.32 in 9.04, 9.10 , 10.04  i still have the wifi connection problems. So i believe that the issue is with 2.6.32 kernel and not ubuntu itself.

I have found several posts with similar problems on other wifi cards. My suggestion is to upgrade the kernel and check if it works for you:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

---

