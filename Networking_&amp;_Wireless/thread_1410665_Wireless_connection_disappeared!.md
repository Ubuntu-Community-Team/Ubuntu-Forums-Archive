---
title: "Wireless connection disappeared!"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by sgtlrc on 2010-02-19
I had no problems using my dell mini with ubuntu wireless UNTIL i did a direct connect into my home network to download some updates.  Now the wireless connection option has disappeared and only shows a wired connection in "network".  Does anyone know how to get it changed back.  Terminal no longer shows an eth1 but lists eth0 as the wired connection on ifconfig.

---

### Post by northd_tech on 2010-02-19
Can you open a terminal window and post the results here when you enter the following commands so that we can determine what kind of hardware you have:

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

---

