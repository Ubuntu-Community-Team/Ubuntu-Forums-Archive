---
title: "2 wan in local"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by ybgwon on 2009-04-09
================= My Office =============================
Wan1 ------- router --- hub --- Network1(192.168.0.0/24)
|
linux-pc-foo --- eth0 (192.168.0.2)
eth1 (100.100.9.2)
|
Wan2(Vpn) --- hub --- Network2(100.100.9.0/24)

==========================================================
Linux pc foo can connect both network. but 192.168.0.3 can't connect 100.100.9.3 directly.

I want to connect directly between Network1 and Network2.

How do I make this work?

---

### Post by superprash2003 on 2009-04-09
you would need to bridge the two interfaces on the linux pc.. [http://ubuntuforums.org/archive/index.php/t-132515.html](http://ubuntuforums.org/archive/index.php/t-132515.html)

---

