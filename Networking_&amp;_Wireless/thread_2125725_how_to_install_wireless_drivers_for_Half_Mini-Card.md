---
title: "how to install wireless drivers for Half Mini-Card, DW1503"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by patriot70 on 2013-03-14
I have a Dell Inspiron N5040 with a DW1503 Wireless-N WLAN Half-Mini Card. I just installed Ubuntu 12.04 today and all is working great except the wireless. It doesn't seen to be recognized.
Does any know the steps to install this card, if possible?
Thanks!!

---

### Post by Hadaka on 2013-03-14
Hi ,please open a terminal ctrl/alt/t  then
copy and paste this command...
```
lspci -n | grep 0280 | awk '{print$3}' 
```

**IF the result is [14e4:4727] then do...
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
**If NOT [14e4:4727] then do..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
copy and paste the results.
thanks.

---

