---
title: "wired network problem"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by ratan797 on 2010-12-03
hi, 
I just install ubuntu 10.10 on my pc. i have winxp also, i have one more network card other then motherbord ethernet port. in window xp both are working fine. but in ubuntu motherbord ethernet port is working but adon ethernet card (realtek RTL-8139/8239C/8139c+) show disconnected.

---

### Post by northd_tech on 2010-12-03
Hi ratan,

Can you open a terminal window under Ubuntu (go to Applications > Accessories > Terminal) and post the results here when you run the following commands?  (You might want to copy & paste the following, especially to get the vertical "pipe" character correct- it usually lives somewhere over by the ENTER key, depending upon your keyboard).

```
lspci 
sudo lshw -C network
ifconfig
iwconfig

```

---

