---
title: "No IP Address?"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by Fajner1 on 2011-06-23
Kubuntu's Network manager says that my (wired) network is in an invalid state because I don't have an IP address, but Firefox and Chorme work perfectly, as do Synaptic and Software Centre, and a Superkaramba network monitor says that my IP is "192.168.1.101"

In fact, the only thing that isn't working is Pidgin, and it says it's "Waiting for network connection."

I don't know what other details I should give.

---

### Post by Iowan on 2011-06-23
Do you (perhaps) have the interface configured in */etc/network/interfaces* ???

---

### Post by Fajner1 on 2011-06-23
Well, the contents of */etc/network/interfaces*:

> 
auto lo
iface lo inet loopback


---

### Post by Iowan on 2011-06-23
> **Fajner1 said:**
> Well, the contents of */etc/network/interfaces*:Hmmm... that appears normal.

---

