---
title: "connected to router but only 10.10 has no internet"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by arzali on 2011-10-18
Hi all,
from one minute to another i cant surf the web on my Ubuntu 10.10 installation.
I can ping the router and have access to its web configuration but i cant open websites like google.com or ubuntu.com.
Now the strange thing is when i start ubuntu 11.10 i have access to the internet.

What could cause such a problem?

---

### Post by praseodym on 2011-10-18
Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
```
Is it LAN/WLAN or both?

---

### Post by arzali on 2011-10-18
Thank you praseodym for your fast respond and sorry that i spent your time
but this is really strange. I rebooted several times and nothing happened but after i checked the host file for changes (there were no changes so i closed it)and rebooted again, everything works:confused:

i will mark this as solved until it happens again.

again sorry

---

