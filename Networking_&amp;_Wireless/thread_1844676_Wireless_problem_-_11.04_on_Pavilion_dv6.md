---
title: "Wireless problem - 11.04 on Pavilion dv6"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by PalapaGuy on 2011-09-15
I just installed Ubuntu 11.04 with Wubi on a new 64-bit (4 GB) HP Pavilion that came with Windows 7.

The laptop wireless works properly under Win 7 but does not activate when I launch Ubuntu 11.04.  The wireless indicator light on the keyboard remains red under Ububtu,  Pressing the button has no effect.

Any ideas will be appreciated.

---

### Post by wildmanne39 on 2011-09-15
Hi, please run these commands in a terminal and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
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

