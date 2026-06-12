---
title: "module does not load properly on boot?"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by ulugeyik on 2006-05-30
Hello,

I have compiled e1000 on 5.10 for kernel 2.6.12-10-386. If I do a manual "rmmod e1000" and "modprobe e1000", it loads fine and I can use the network card (on IBM T60 laptop).

However, I can not get this to be loaded up properly during boot-up. I added it to the end of /etc/modules  and created /etc/modprobe.d as "alias e1000 eth0". It seems to me that it loads the *wrong* module or some such thing because it gives an error in dmesg:

[4294679.368000] e1000: 0000:02:00.0: e1000_sw_init: Unknown MAC Type
[4294679.368000] e1000: probe of 0000:02:00.0 failed with error -5

if I do a manual "rmmod e1000" and "modprobe e1000", then it works fine.

Any idea how I could resolve this?

---

