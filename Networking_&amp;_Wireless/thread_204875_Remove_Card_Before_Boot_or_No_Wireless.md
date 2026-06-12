---
title: "Remove Card Before Boot or No Wireless?"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by bluevoodoo1 on 2006-06-27
I just bought a Netgear wg511T wireless card. I haven't had the wonderful joy of working with wireless with Ubuntu until now, so I'm a wireless novice. It seems to work well, but only if it is not inserted during boot up. If I insert it after I have logged in then it is fine. 

Is there anyway to have wireless work without removing/inserting the card after every shutdown and before every startup?

---

### Post by bluevoodoo1 on 2006-07-08
Any ideas?

---

### Post by bluevoodoo1 on 2006-09-04
I got it, here's my Network Interfaces file if anyone wants to see. 

> 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
auto ath0
iface ath0 inet dhcp
wireless-essid xxxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxx




---

