---
title: "not able to connect to internet in 9.04"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by karthik_jce on 2009-06-16
Hi,

I installed ubuntu 9.04 in my pc, I have a Netgear WG111 wireless adapter. Ubuntu 9.04 detected the device correctly and connected to my wireless network. but I am not able to browse any of the sites, even I am not able to ping them. I see that the name resolution happens and then ping doesnt succed.

Any suggestions on how to get this to work ?

I am able to ping the wireless router gateway.

Regards
Karthik

---

### Post by papangul on 2009-06-16
Try to use Opendns as your dns server:
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by alphacrucis2 on 2009-06-16
What does this give:

```
route -n
```

---

### Post by superprash2003 on 2009-06-16
post output of **sudo iptables -L**

---

### Post by andrewlinn957 on 2009-07-16
Nevermind; I've solved the issue.

The problem was that I had edited the etc/network/interfaces file in order change to a static IP for port forwarding. I reverted to the backup and then ran > sudo /etc/init.d/networking restart which solved the issue

---

