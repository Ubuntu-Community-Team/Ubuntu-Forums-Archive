---
title: "ssh and wireless network card"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by linux-beginner on 2011-04-12
Hi,
Yesterday I installed a RaLink RT2800 802.11n PCI on my squeeze system. Now I have a connection to Internet but I can not connect other systems in my home network.
An ssh-try to a system in my home network results in:
ssh: connect to host xxx.xxx.xxx.xxx port 22: No route to host

If I use my eth0, I do not have connection to Internet, but I can connect other systems in my home network.
Could somebody tell me what is wrong?
Thanks,

---

### Post by gareththered on 2011-04-12
Can you ping the host you are trying to ssh to?

---

### Post by pricetech on 2011-04-12
How are your NICs connected ??  Do the rest of the computers on the network have Internet ??  If so, how are they connected ??

Also, how is your wired NIC configured ??

---

