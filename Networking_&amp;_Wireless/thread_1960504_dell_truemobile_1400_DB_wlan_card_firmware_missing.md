---
title: "dell truemobile 1400 DB wlan card firmware missing"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by Dark Source Tech on 2012-04-17
hey everyone 

im new to the ubuntu so before throwing it on my new laptop i put it on my old one
(dell Latitude d500)
but when i try to hook up to wifi it says 
Wireless Not Ready (firmware Missing)

the card is a Dell Truemobile 1400 DualBand Minicard

any help is great and thanks in advance

---

### Post by chili555 on 2012-04-17
Let's find out a bit more about your wireless card. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

