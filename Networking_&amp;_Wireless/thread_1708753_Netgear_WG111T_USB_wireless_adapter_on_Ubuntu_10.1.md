---
title: "Netgear WG111T USB wireless adapter on Ubuntu 10.10"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by Puzzettone on 2011-03-17
Hi, I'm going to install **Ubuntu 10.10** on my old desktop computer in dual boot with Windows XP. As for the internet connectivity, I have a Netgear [WG111T]("http://kb.netgear.com/app/products/model/a_id/2559") USB wireless adapter, that works flawless under Windows XP. Of course it is vital that this Wi-Fi adapter works in Ubuntu too. On the web I've found many installation guides for this piece of hardware but they refer to older versions of Ubuntu. What should I expect with Ubuntu 10.00? Will it automatically recognize the USB adapter? If not, what install procedure do I have to follow?
Thank you.
P.

---

### Post by chili555 on 2011-03-17
As you can see here, there are two different versions of WG111T. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB)

Can you please run the live CD and insert the device and open a terminal and run and post:```
lsusb
```Then we can advise you further.

---

### Post by Puzzettone on 2011-03-17
lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1385:4251 Netgear, Inc WG111T (no firmware)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2011-03-17
Here is a pretty good tutorial.

[http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/](http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/)

Post back if you get stuck.

---

### Post by PCNetSpec on 2011-03-30
I know it's an old(ish) post, but for future readers..

Don't use ndiswrapper, there are Linux native drivers for the Netgear WG111T.

Instructions here:
[http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572](http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572)

---

