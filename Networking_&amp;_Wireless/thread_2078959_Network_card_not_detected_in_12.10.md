---
title: "Network card not detected in 12.10"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by prasannakumar1117 on 2012-11-01
Hi all,

I am new to ubuntu & i have installed ubuntu 12.10 in my laptop toshiba c850.

But the network card has not been detected and the wireless too not working can anyone help me plz.

regards,
Prasanna

---

### Post by chili555 on 2012-11-01
Let's find out what kind of wireless card you have. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

