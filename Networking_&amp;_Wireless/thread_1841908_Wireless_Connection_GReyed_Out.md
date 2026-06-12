---
title: "Wireless Connection GReyed Out"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by Coba on 2011-09-10
Any ideas why I can see my wireless router in Ubuntu 10.4. But it is greyed out and there is nothing I can do to make a connection with it?

---

### Post by wildmanne39 on 2011-09-10
Hi, welcome to the forum! please run these commands in a terminal and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

