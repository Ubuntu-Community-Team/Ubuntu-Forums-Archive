---
title: "ssh: Segmentation fault"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by aleister crowley on 2011-04-01
Today I was using ssh, but happened an error when I tried connect to a server:
*Segmentation fault*

I took a look in the /var/log/messages and saw:
*Apr  1 17:23:31 dtbd13 kernel: [ 2115.471762] ssh[3040]: segfault at 2d000000c0 ip 00007ffe86e5c052 sp 00007fff84261208 error 4 in libc-2.11.1.so[7ffe86dd9000+17a000]*

I reinstalled openssh and libc6, but it didn't solve my problem.

Any suggestions?

Thanks!

---

