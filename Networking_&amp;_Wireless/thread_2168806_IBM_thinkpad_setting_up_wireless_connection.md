---
title: "IBM thinkpad setting up wireless connection"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by guybo211 on 2013-08-19
I have just installed xubunto 13.04 on an old IBM ThinkPad. Wireless does not work. Have a D-Link wireless DWA-652 card installed MAC id 0022BOCCB801. I am sending this from another computer connected via home wireless. Help?

---

### Post by praseodym on 2013-08-19
Hi,

first: please remove your MAC address for security reasons ;)

2nd: Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk
lsmod
iwconfig
cat /etc/resolv.conf
route -n
rfkill list
```
You can c/p the outputs into a text file and paste it in here

---

