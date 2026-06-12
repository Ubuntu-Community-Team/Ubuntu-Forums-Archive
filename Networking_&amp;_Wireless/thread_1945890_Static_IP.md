---
title: "Static IP"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by Major Payne on 2012-03-23
Currently I'm running ubuntu server 11.04 with the kde gui on top.

I'm having problem getting my static ip to work. i'm attempted in the interface file and it failed to connect to anything. 

I have even attempting in the KDE Networking interface and still uses DHCP can someone please help me i know it's a small thing i'm missing

---

### Post by papibe on 2012-03-24
Hi Major Payne.

It may be required to restart your machine after that change. Alternatively, you can try this:
```
sudo service network-manager restart
```
Hope it helps,
Regards.

---

### Post by lisati on 2012-03-24
This is just my preference, but I usually find it easier to let my router hand out IP addresses, setting it to reserve addresses for specific machines as required.

---

