---
title: "send traffic from [pc1] to [pc2] to [wireless], how?"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by loolooyyyy on 2012-04-14
pc1 has eth0 and is connected to pc2 via eth0
pc2 has eth1 which is connected to pc1
also pc2 has wlan0 which is connected to router, router is connected to internet
this setup can not be changed in anyway (physically i mean! only configs)

now, pc1 wants to connect to internet too, how do we setup iptables for this? on pc2 i mean

(i think i said everything clearly, because this is not about ad-hoc, we don't want to touch the wlan0<->router connection at all! or maybe imagine we dont even have wlan0, just eth2, we want to send traffic from "eth1 on pc2" [comming from pc1] to "eth2 on pc2" which is connected to internet)

any suggestion is welcome :D

yessss! i think what i mean!!! ubuntu as gateway

---

### Post by loolooyyyy on 2012-04-14
beautifully explained here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
i was so dumb finding it after 2hours...

---

