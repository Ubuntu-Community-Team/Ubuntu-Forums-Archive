---
title: "[HELP]Can't see any wireless network on ubuntu 12.04"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by aciang2 on 2013-08-04
last night , i installed ubuntu 12.04 LTS 64bit on my laptop completly .
but after that , i can't connect any wireless because i didnt see any wireless network .
i already browsing about this , and try many instruction but still cant see any wireless network .
can somebody help me? im really frustrating like im gonna change back to windows .

Thanks!

---

### Post by TheFu on 2013-08-04
> **aciang2 said:**
> last night , i installed ubuntu 12.04 LTS 64bit on my laptop completly .
but after that , i can't connect any wireless because i didnt see any wireless network .
i already browsing about this , and try many instruction but still cant see any wireless network .
can somebody help me? im really frustrating like im gonna change back to windows .

Thanks!

This tools are you using to attempt this?
Have you tried any others?
Is the wifi radio on in your PC?  Sometimes hitting the wrong Fn+## key can disable it.
What do the log files show related to wifi?

With great power comes great responsibility.

---

### Post by praseodym on 2013-08-04
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```
Does LAN work?

---

