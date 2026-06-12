---
title: "Cannot install Dell Inspiron wireless card(Broadcom Bcm 4312)"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by SchrodingerCat on 2013-09-03
Hi,
i know there are other posts about the same problem but i can-t find a solution!
I installed Linux many times with no problem at all but now i can-t get my 
wireless card working. 
This is the message i got:
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

Thanks for helping

---

### Post by cariboo on 2013-09-03
Moved to Networking & wireless, as this is a bit more than a beginner question.

Depending on the version, the BCM4312, uses either the b43 or bcmwl driver, do you remember which one was used in previous installs?

---

### Post by Hadaka on 2013-09-03
Hi,please post the output of..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list
```
thanks

---

