---
title: "Dell Latitude E5520 - Wireless Network Card not Found"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by dschild on 2012-05-09
Just upgraded to 12.04 LTS. Since the upgrade Ubuntu does not recognize my network card. I know on my previous version of Ubuntu I had to make changes to configuration, but I don't remember what that was. 

Suggestions?

---

### Post by chili555 on 2012-05-09
Let's ask your computer what kind of card it has. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by dschild on 2012-05-09
Broadcom Corporation BCM43228 802.11a/b/g/n

---

### Post by dschild on 2012-05-09
Ok, after you helped me find my card, I found the following solution, which worked.

> Sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install bcmwl-kernel-source

---

