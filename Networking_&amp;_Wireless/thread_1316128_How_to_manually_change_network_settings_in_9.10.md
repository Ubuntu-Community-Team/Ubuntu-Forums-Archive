---
title: "How to manually change network settings in 9.10"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2009-11-05
How do you manually modify the network setting (static ip, gateway, submask and such) in 9.10.

It use to be in /etc/network/interfaces; but that does not appear to be the case in 9.10.

Thanks,

---

### Post by b0b138 on 2009-11-05
right click the network manager applet (up by the clock), edit connections

---

### Post by Iowan on 2009-11-05
t least in Jaunty, you could set up a manual connection (as mentioned) via Network Manager - as well as via */etc/network/interfaces*.

---

### Post by weaver4 on 2009-11-05
I need to do it manually.  

The final goal is to write a bash script that will modify the network parameters, and then restart networking.

---

### Post by b0b138 on 2009-11-07
Try removing the network manager package as that might be overriding the interfaces file.

---

