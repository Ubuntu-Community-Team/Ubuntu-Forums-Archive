---
title: "eth0 keeps forgetting IP"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Mazin on 2010-05-15
I've set up Internet connection sharing, with Internet from wlan0 being shared to eth0 locally.  Interface eth0 has the IP 192.168.0.1, since it's the gateway.  Problem is, every time eth0 is disconnected, it forgets its IP, and then nothing works until I ```
ifconfig eth0 192.168.0.1
``` again.

Is there a way to permanently set the IP for eth0 to 192.168.0.1 so that it's remembered across disconnects?

---

### Post by mhgsys on 2010-05-15
Set the ip in the network manager;

Right click it; edit connections

---

