---
title: "WMP200 cannot be reached from clients"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by windwalker78 on 2010-03-19
The problem is noticed on Ubuntu 9.04 and 9.10. The Linksys WMP200 card is recognized and works fine, but other clients cannot see the machine until it pings them. The problem is related to power management of the Wi-fi Card. What I did is:

iwconfig wlan0 power off

Hope this helps someone :)
Todor

---

