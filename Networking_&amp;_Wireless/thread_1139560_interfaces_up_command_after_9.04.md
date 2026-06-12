---
title: "interfaces up command after 9.04"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by AntariusX on 2009-04-27
Hello.
 
I just upgraded to 9.04 and everything went fine except one thing.
 
auto eth0:0
iface eth0:0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
**up ip route add xxx.xxx.xxx.xxx via xxx.xxx.xxx.xxx**
 
ip route command doesn't work anymore. It did work in 8.10. What has changed and how can i make it work again?

---

### Post by AntariusX on 2009-05-05
UP. No one had it? I tryed post-up, up, it did worked great in 8.10, but in 9.04 it won't.

---

