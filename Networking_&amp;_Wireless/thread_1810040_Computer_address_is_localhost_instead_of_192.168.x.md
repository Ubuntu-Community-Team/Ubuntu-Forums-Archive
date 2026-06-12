---
title: "Computer address is localhost instead of 192.168.x.x"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by emurad on 2011-07-22
Hi,

One of the computers attached to the network is giving localhost instead of 192.168.x.x in Remote Desktop config page therefore I'm unable to access it:

> Your desktop is only reachable over the local network. Others can access your computer using the address localhost.Other computer and even other accounts on the same computer are showing something like:

> Your desktop is only reachable over the local network. Others can  access your computer using the address 192.168.0.8.How can I fix this?

Thanks.

---

### Post by spiky001 on 2011-07-22
Have you tried setting a static ip address, see if that fixes problem.

---

### Post by papibe on 2011-07-22
Could you post the following files:
```
/etc/hostname
/etc/hosts
```
And also the result of these commands:
```
$ ifconfig

$ route -n
```
Regards.

---

