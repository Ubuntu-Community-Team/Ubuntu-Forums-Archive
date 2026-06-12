---
title: "WLAN adapter completely deactivated by NetworManager"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Rschnauzer on 2009-12-26
After taking off the mark "wirelessnetwork aktivate" from NetworkManager drop down menu the adapter was completely deactivated in Ubuntu and I did not find any way to reactivate it.
Rebooting Vista also did not see the adapter (power standby does not help).
Only complete disconnect the PC from power and booting Vista reactivates the adapter (driver rt287xusb).
After this bypass procedure, NetworkManager again sees the adapter.

I normally use the eth0 adapter and wlan0 only produces messages to the log.
How may I deactivate/activate the WLAN adapter in NetworkManager?

---

### Post by bender1234 on 2009-12-26
Hi.

It doesn't work to right click the icon and disable/enable wifi?

Also have you blacklisted the rt2800usb driver?

sudo /etc/init.d/networking restart prolly doesn't help either? It just ignores the interfaces config as you are using network manager?

bender

---

### Post by Rschnauzer on 2010-01-18
> **bender1234 said:**
> ...It doesn't work to right click the icon and disable/enable wifi? Also have you blacklisted the rt2800usb driver?

Only disable no enable possible.
blacklisting with modprobe -rf rt2800usb kills the system.

[edit]: problem with disable/enable is no more reproducible

---

