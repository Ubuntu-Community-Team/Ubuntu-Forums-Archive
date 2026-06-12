---
title: "Statically associate ethernet interface with network connection"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by aakash.ece on 2011-03-29
I've been looking for it and didn't find it on internet - discovered it just now, so sharing (pardon me if its a repeat):

**My scenario**: I've got two Network interfaces on my 10.04 powered laptop - eth0 and eth1.
I keep carrying my laptop around the office, where I keep connecting "eth1" to different (wired) domains on different floors (they don't have DHCP). For this purpose, I've made many manually configured network connections (say 192.168.0.341, 192.168.13.56 and 10.0.15.46), and choose the relevant one manually by clicking on nm-applet.

**My problem:** was that I couldn't get nm to pick a "default" connection of my choice whenever I connected an ethernet cable to eth1. i.e. it would always pick 192.168.13.56, but that what not I wanted. I wanted to make, say, 10.0.15.46 as the default, because that's what I mostly need.

*In general, I couldn't find a way to associate a static IP with an interface* (using network-manager. Ofcourse you can do it by manually editing /etc/network/interfaces)

**The solution:**
Is to simply put the mac address of the interface you want in the network connection you wish to make as default.
So, if my eth1's mac address is 00:02:45:AA:BB:CC, I can open System->Preferences->network connections->10.0.15.46->edit and put "00:02:45:AA:BB:CC" in the mac address and voila! Whenever I plug a cable in eth1, it always picks 10.0.15.46 now by default :)!

You can use this to "statically" couple the network config with the interface using ubuntu network manager.

---

