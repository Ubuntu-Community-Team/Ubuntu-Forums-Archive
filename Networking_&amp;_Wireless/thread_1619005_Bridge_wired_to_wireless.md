---
title: "Bridge wired to wireless"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by tunco on 2010-11-11
Hi,

I have wired connection and have wireless adapter. I connect to internet with wired. I created new wireless network on my desktop. My laptop connected to my new wireless network but i can't connect to internet and my desktop can't connect to internet too when I select option "shared other computers" on my wired connection. How to bridge wired and wireless on my desktop.

---

### Post by nsblenin on 2010-11-11
copy here your IP table:

route -n

---

### Post by tunco on 2010-11-11
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by tunco on 2010-11-12
I think there is no body in here for support : (

---

### Post by spiky001 on 2010-11-12
did you try sharing wireless connection

---

