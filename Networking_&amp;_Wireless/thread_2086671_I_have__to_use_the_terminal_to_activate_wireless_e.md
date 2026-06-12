---
title: "I have  to use the terminal to activate wireless each time"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by ve3rpm on 2012-11-21
I have a Dell inspiron 1525 of a friend who finally wants ubuntu... I installed 12.10, and got the wireless to work, however each time it's turned off I have to modprobe b43 to get wireless.  I really don't want this to be her intro to ubuntu.  Please help!  thanx.

---

### Post by wildmanne39 on 2012-11-21
Hi, please do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by ve3rpm on 2012-11-21
Wow!  Thanx so much!  Worked first time.

---

### Post by wildmanne39 on 2012-11-21
Your welcome!
Enjoy

---

