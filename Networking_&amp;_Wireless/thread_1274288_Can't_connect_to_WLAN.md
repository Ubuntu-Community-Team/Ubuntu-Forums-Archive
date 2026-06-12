---
title: "Can't connect to WLAN"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by sebastiaopburnay on 2009-09-24
Hi, I have installed a wuindows driver [blkgu] using ndiswrapper so that I can use a wireless USB adapter [ID 050D:705E].

Everything seems fine, **ndiswrapper -l** retrieves the expected:

[B]blkwgu : driver installed
         device (050D:705E) present (alternative driver: rtl8187)[/B]

Network manager recognizes a phew WLANs including my own, to which I want to connect (the access is controlled by MAC address solo and I've inserted the WIFI adapter's MAC on the router's table). The problem is that I can't get connected to the WLAN.

Thank you

---

### Post by amingv on 2009-09-24
Did the native driver give you any trouble? It is posible that you have not disabled the older driver (rtl8187), and it's still being used. Blacklisting the driver would be the choice in that case.

Also make sure the ndiswrapper module is loaded:
```
modprobe -l | grep ndiswrapper
```

---

### Post by sebastiaopburnay on 2009-09-24
Yes, I've done that before, using the graphical app (ndisgtk) to remove the realtek driver, the only one left is the blkwgu, ndisgtk even recognizes the device as being present. Though, the problem remains.

---

