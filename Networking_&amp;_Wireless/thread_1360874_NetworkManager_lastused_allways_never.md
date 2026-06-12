---
title: "NetworkManager lastused allways never"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by Rschnauzer on 2009-12-21
NetworkManager allways displays "never" for "last used" with each connected interface.

How may I configure network manager to see whether an interfaced had been used?

---

### Post by Iowan on 2009-12-21
Is NM managing the interface(s) - or is it (are they) configured via */etc/network/interfaces*? NM will know nothing about it/them... but *might* be convinced to manage it (probably one at a time) anyway.

---

### Post by Rschnauzer on 2009-12-22
Thanks,
I did not do anything with  [I]/etc/network/interfaces, eth0 had been automaticly defined in NetworkManager and I added the wlan later. 
eth0 is activated automaticly after boot but status always shows last used never. How may I convince NM to change status?
[/I]

---

### Post by Iowan on 2009-12-22
Perhaps you could post */etc/network/interfaces*.

---

### Post by Rschnauzer on 2009-12-22
Hallo,

*following /etc/network/interfaces*
auto lo
iface lo inet loopback

eth0 is automatically active in NetworkManager
wireless (wlan0) is deactivated and I don't know how to activate it

---

### Post by Rschnauzer on 2009-12-26
I found a bypass to the problem:

If you mark on interface entries LAN and WLAN "use for all users" no time stamp is set.
If you don't mark it, last used is set correct.

Seems to be an access permission problem. I don't know how to solve it for "all users".

---

