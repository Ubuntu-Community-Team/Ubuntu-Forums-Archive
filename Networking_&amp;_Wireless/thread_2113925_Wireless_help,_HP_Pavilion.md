---
title: "Wireless help, HP Pavilion"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by epxrambo on 2013-02-08
i have a hp pavilion and it use to have os but i removed it. thats why i download ubuntu but my problem is the wireless switch on my laptop doesnt work anymore is there a way to fix it?

---

### Post by chili555 on 2013-02-08
Do you have a working wireless interface? Please open a terminal and run and post:```
iwconfig
rfkill list all
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

