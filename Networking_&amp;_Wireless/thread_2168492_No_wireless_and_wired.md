---
title: "No wireless and wired"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by davoudi on 2013-08-18
Hi Everyone,

 My Ubuntu crashed yesterday and after that I lost my connection to internet. The icon for wired shows on and everything seems correct but there is no connection. The wireless icon is off and I cannot turn it on. It says that that hardware is disabled. My ubuntu is 12.04 and my laptop is sony. Thank you very much in advance for your help.

---

### Post by davoudi on 2013-08-18
I resolved the problem by adding the following line in the file interfaces inside etc/network

auto eth0
iface eth0 inet dhcp

and then

sudo service networking restart

Thanks

---

