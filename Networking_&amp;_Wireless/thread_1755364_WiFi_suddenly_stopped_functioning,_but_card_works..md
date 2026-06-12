---
title: "WiFi suddenly stopped functioning, but card works."
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by mykeld on 2011-05-11
I was uninstalling some programs through the package manager, then restarted. When my netbook turned back on, I had no internet connection and the WiFi icon wasn't showing in the notification area as it usually does either. Says the card is functioning properly and everything. Other devices can connect to the WiFi. I'm kind of new to Ubuntu and searched around a bit, but am at a loss. Can anyone help?

HP Mini 110
Ubuntu 10.10
Broadcom BCM4313

Edit: > $ sudo ifconfig -s  shows that the device is not running..

---

### Post by northd_tech on 2011-05-11
For a Broadcom "4313"- try this thread:

[http://ubuntuforums.org/showthread.php?t=1748245](http://ubuntuforums.org/showthread.php?t=1748245)

---

### Post by mykeld on 2011-05-11
That thread didn't really help, and it's pretty confusing to follow. I'm a complete noob.. :(

Anyone else? I'm desperate :P

---

### Post by josephmills on 2011-05-11
hi there could you please open your terminal (ctrl+alt+t) and type in ```
lspci -vnn | grep 14e4 
``` and post it here also could you post ```
rfkill list all 
```thanks

---

