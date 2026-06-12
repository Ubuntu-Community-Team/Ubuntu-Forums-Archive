---
title: "wireless pppoe connection"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by KRISHNASHK on 2012-01-18
how to create a wireless pppoe connection in ubuntu ??, i have username and password of my ISP..
thanks in advance

---

### Post by praseodym on 2012-01-18
Try

```
sudo pppoeconf
```

in a terminal (CTRL+ALT+T) or use the rider "DSL" in the network-manager applet.

---

### Post by KRISHNASHK on 2012-01-21
that works only if i have a wired connection. how about the wireless connection, i am connected over wifi.?

---

### Post by praseodym on 2012-01-21
Try

```
sudo pppoeconf wlan0
```

---

### Post by KRISHNASHK on 2012-01-22
> **praseodym said:**
> Try

```
sudo pppoeconf wlan0
```
my wifi adapter is working , i want to connect to my router through which i should create a pppoe connection!!

---

### Post by KRISHNASHK on 2012-01-22
> **KRISHNASHK said:**
> my wifi adapter is working , i want to connect to my router through which i should create a pppoe connection!!
i created pppoe connection in my router it self. problem solved. any ways thanks for the support!!!

---

