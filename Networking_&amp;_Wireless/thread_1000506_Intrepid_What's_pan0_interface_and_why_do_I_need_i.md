---
title: "Intrepid: What's pan0 interface and why do I need it"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by mibadt on 2008-12-03
Hi,
I'm on a new install Kubuntu Intrepid connected to a LAN/router via eth0. My Firestarter (fw) found a pan0 interface (with no communication so far) which I'm sure wasn't there in former Kubuntu installations (same hardware and network).

I found the following in dmesg:
root@Miki-Desktop:/home/miki# dmesg | grep pan
[    0.404025]  domain 0: span 0 level CPU
[   38.737888] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
------
What's this pan0 interface, do I need it? If not-how do I "eliminate" it, if yes-how do I secure it.

---

### Post by puppywhacker on 2008-12-03
Personal Area Networking Profile (PAN) allows Bluetooth devices to form an ad-hoc network, access a remote network through a network access point.

if it doesn't show in "ifconfig" it is not activated.

---

### Post by mibadt on 2008-12-03
Solved
 Changed to zero (from 1) the BLUETOOTH_ENABLED entry in /etc/default/bluetooth.

Regards,
Michael Badt

---

