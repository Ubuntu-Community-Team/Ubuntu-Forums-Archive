---
title: "Dell wireless card not working"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by IDEAgeophysics on 2010-01-20
I have installed ubuntu 9.10 as a second OS after windows XP on my Dell Inspiron 1520 and cannot get the wireless working.  My wireless is a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card Rev 2.0.  When I try to look for networks the only thing i can get is suggestions for a wired connection, but I don't have access to one.  

Any suggestions on how to connect to wireless with passcode protected WPA connections?  Thanks in advance.

---

### Post by bkratz on 2010-01-20
> **IDEAgeophysics said:**
> I have installed ubuntu 9.10 as a second OS after windows XP on my Dell Inspiron 1520 and cannot get the wireless working.  My wireless is a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card Rev 2.0.  When I try to look for networks the only thing i can get is suggestions for a wired connection, but I don't have access to one.  

Any suggestions on how to connect to wireless with passcode protected WPA connections?  Thanks in advance.

Usually the Dell cards are simply relabeled Broadcoms. You can find out by typing lspci in the terminal and looking for the wireless device. (LSPCI in lowercase). The terminal is at Applications>>Accessories>>Terminal

If it is a Broadcom device it will probably say something like
BCM43xx.

You can then look here.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by IDEAgeophysics on 2010-01-20
Thanks! Very useful.  Did not know it was Broadcom

---

