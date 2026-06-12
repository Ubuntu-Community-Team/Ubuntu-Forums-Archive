---
title: "Network Manager has a mind of it's own! [Help]"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by infinity404 on 2012-02-21
I have a Broadcom 4313 wireless card in my laptop, running Ubuntu 11.10 64 bit. I can install the STA driver fine using ethernet, but network manager doesn't acknowledge the existence of the wireless interface. 

Installing WICD allows me to connect to my wireless network, and works maybe ~30-50% of the time. The other times, it claims to be connected, and running ifconfig & iwconfig shows that the computer is connected to the network with valid IP address but I am unable to ping anything, and paged don't resolve.

Any help either getting network manager to utilize the card correctly or getting WICD to work properly would be extremely appreciated.

---

### Post by praseodym on 2012-02-21
Hi,

for the driver issue see here: [http://ubuntuforums.org/showpost.php?p=11707164&postcount=2](http://ubuntuforums.org/showpost.php?p=11707164&postcount=2)

You should use only Wicd or NM, both dont work well in parallel

---

### Post by infinity404 on 2012-02-21
I uninstalled NetworkManager before installing WICD, so I doubt that that is the issue.

---

