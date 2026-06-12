---
title: "eth0, eth1, wlan0, wlan1 ¿how to know?"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2009-03-03
I have a wireless card.
Lspci shows it.
But ¿how to know what name I need to set in /etc/network/interfaces?
¿how to know the name of the ethernet the card is waiting for to proceed with ifconfig up?
Thanks!

---

### Post by japsai on 2009-03-03
try ```
iwconfig
```.

---

### Post by dmizer on 2009-03-03
Post the output of:
```
lshw -C network
```

---

### Post by jmvidalvia on 2009-03-03
> **dmizer said:**
> Post the output of:
```
lshw -C network
```
Yes!
That's what I was looking for, the logical name.
Thanks a lot!

---

