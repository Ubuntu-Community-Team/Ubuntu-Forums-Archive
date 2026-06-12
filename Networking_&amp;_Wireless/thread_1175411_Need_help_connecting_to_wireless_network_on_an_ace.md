---
title: "Need help connecting to wireless network on an acer aspire one netbook"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by funkyali on 2009-06-01
Hi,

I have been able to connect to my wireless network with no problem until a few days ago when I tried to install Wine and vitual box. I then updated the recommended system updates which did not work. I then upgraded from 8.10 to 9.04 which now I can see the wireless option under the network connection icon but it does not show any wireless networks.

I dual boot and have no problem connecting with XP.


Any advise really appreciated.

---

### Post by coffeeaddict22 on 2009-06-01
Hi,
Can you open a terminal, type in the following commands, and post back the output (put a code box around it to make it easier to read- it's the hash icon above the box you type in).
```
lspci
lshw -C network
sudo iwconfig
```
minus the address data we don't want to see.

---

