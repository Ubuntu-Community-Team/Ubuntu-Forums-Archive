---
title: "Ralink RT2800 chipset / rt2860 driver"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by Raiju on 2010-02-06
Is there a Better driver then the default driver provided by ubuntu?
In games i tend to get ping spikes randomly.
Network manager shows the connection speed spiking from 54mb\s, 35mb\s to 5mb\s

I using a Tenda w322p(RaLink RT2800 802.11n PCI)

---

### Post by chili555 on 2010-02-06
How about letting us see, in a terminal:```
lsmod | grep rt2
lspci -nn | grep Network
```Thanks.

---

### Post by Raiju on 2010-02-06
```
lsmod | grep rt2
rt2860sta             579308  1 

lspci -nn | grep Network
03:08.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601] 
```

:D

---

### Post by chili555 on 2010-02-06
I know of no other current driver, either in the kernel or on Ralink's site. They have a 2860 driver for Linux, but it's a little old and probably wouldn't compile correctly. You might google the device ID: 1814:0601

---

