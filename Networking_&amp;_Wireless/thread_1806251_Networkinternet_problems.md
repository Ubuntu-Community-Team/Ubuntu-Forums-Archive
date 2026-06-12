---
title: "Network/internet problems"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by carsten on 2011-07-17
Hi
I just installed the 64 bit version of Ubuntu 11.04 (with some difficulties)
The problem is that i loose my internet connection with regular intervals - every 2-3 mins the internet connection is off for 1-2 mins and on top of that im not able to reach more than 250 kb/s from any site when downloading - tried the same sites on the same machine using Windows 7 and it ran 1000kb/s+.
I have never had this issue with Ubuntu before so it baffles me a bit.
When i did a 'dmesg' it was cluttered with this (also was the the log during installation)
.
.
.
[ 3947.098850] r8169 0000:04:00.0: eth0: link up
[ 3948.903234] r8169 0000:04:00.0: eth0: link up
[ 3954.027302] r8169 0000:04:00.0: eth0: link up
[ 3957.875335] r8169 0000:04:00.0: eth0: link up
[ 3958.832367] r8169 0000:04:00.0: eth0: link up
[ 3959.360744] r8169 0000:04:00.0: eth0: link up
[ 3970.077429] r8169 0000:04:00.0: eth0: link up
[ 3972.958470] r8169 0000:04:00.0: eth0: link up
[ 3974.104898] r8169 0000:04:00.0: eth0: link up
[ 3984.034001] r8169 0000:04:00.0: eth0: link up
[ 3985.280120] r8169 0000:04:00.0: eth0: link up
[ 3988.141247] r8169 0000:04:00.0: eth0: link up
[ 4030.100761] r8169 0000:04:00.0: eth0: link up
.
.
.
doing an lspci tells me that i have a r8168 so the r8169 buggles me even more. Can anyone cast some light?
(even submitting this post took 3 mins)

---

### Post by jmoorse on 2011-07-17
Please check this post:

[http://ubuntuforums.org/showthread.php?t=1805271](http://ubuntuforums.org/showthread.php?t=1805271)

---

### Post by carsten on 2011-07-17
Thanks, that seemed to have solved it :)

---

### Post by carsten on 2011-07-17
Altough, my r8168 no longer auto loads on startup - how would i make it do that again?

---

