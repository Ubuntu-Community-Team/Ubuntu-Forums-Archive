---
title: "service networking restart doesn't reflect changes to /etc/network/interfaces"
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by troypiggo on 2012-11-08
On a fresh Ubuntu 12.04.01 LTS installation I'm finding that if I make changes to '/etc/network/interfaces' and try to do a 'service networking restart', the changes made in the interfaces file aren't reflected in a 'ifconfig'.

I'm pretty sure this behaviour is different on my previous versions (Lucid etc).

If you make changes to that interface file, how do you get the networking and ifconfig to update to those changes?

---

### Post by ahallubuntu on 2012-11-08
If you are using Ubuntu Desktop (not server) edition, then you are probably using Network Manager, and that will override the settings in that interfaces file.

---

### Post by troypiggo on 2012-11-09
No, it's a virtual server, not a desktop.  Console only.

Any ideas?

---

### Post by varunendra on 2012-11-11
There have been some changes in 12.04 regarding network configuration, but they are limited to resolv.conf only AFAIK. Please refer to : [https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution)

If what you are trying is not addressed there, please post the contents of the *interfaces* file and the desired changes you want to make. Also, the output of *ifconfig*.

---

