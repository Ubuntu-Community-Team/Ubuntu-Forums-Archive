---
title: "Connect To Unprotected HotSpot Using Only Command Line"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by nythacker on 2009-03-04
Hi,

Can anybody show me how to **search** and **connect** to an _unprotected/open_ wifi hotspot (e.g. Internet Cafe, hotels, airports, etc.) using _only_ the command line?

Any help would be greatly appreciated. Thanks!

---

### Post by nythacker on 2009-04-18
Anyone... please???

---

### Post by prshah on 2009-04-18
> **nythacker said:**
> 
Can anybody show me how to **search** and **connect** to an _unprotected/open_ wifi hotspot (e.g. Internet Cafe, hotels, airports, etc.) using _only_ the command line?


```
sudo iwlist wlan0 scan
```Give the list of Access Points and Ad-Hoc cells  in  range,

```
sudo iwconfig wlan0 essid "ACCESSPOINT"
``` to connect to "ACCESSPOINT"

..and, since these _usually_ use dhcp```
sudo dhclient wlan0
``` If all these three work without errors, you should now be connected.

Replace wlan0 with the actual name for your wireless interface.

Use responsibly.

---

### Post by nythacker on 2009-04-19
Thank you so much, prshah! You just made my day...

---

