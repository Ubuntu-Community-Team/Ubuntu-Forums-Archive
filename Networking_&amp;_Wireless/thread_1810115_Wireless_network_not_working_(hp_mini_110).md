---
title: "Wireless network not working (hp mini 110)"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by S-cube on 2011-07-22
i have recently installed ubuntu 11.04 on my hp mini 110. Unfortunately it does not connect to the wireless network because of missing firmware. I would be very thankful if you could help me in this regards.

---

### Post by wildmanne39 on 2011-07-22
Hi, run these commands in a terminal
```
lspci -nn
```
```
iwconfig
```
```
rfkill list All
```

---

