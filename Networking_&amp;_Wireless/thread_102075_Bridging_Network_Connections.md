---
title: "Bridging Network Connections"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by simon_7_1_8 on 2005-12-11
Hi guys... I have two LAN cards in my pc, both of which are connected to my router. When i try to connect to the internet while both cards are activated, it doesnt work, although i can still get to my routers configuration page fine. With only one card activated, however, it works fine. 

I was trying to find somewhere in the network settings that would allow me to bridge the network connections, like you can in windows, as i thought doing this might fix the problem? Or can anyone offer any other advice?

---

### Post by ape on 2005-12-11
Umm.. bridging is to be used to connect two different networks together.  If you have both of these NICs plugged into your router, you really don't have two different networks.  What exactly are you trying to accomplish?

---

### Post by simon_7_1_8 on 2005-12-12
I want to be able to use both of the network adapters at the same time to connect to the router, but i have to pick one of them to be my default network device or something like that, thats why i thought of whether or not it would be possiblt to bridge them into 1 connection

---

### Post by sirlancelot on 2005-12-15
If, by connecting two cables from your router to a single computer you hope to acheive a faster connection, you would be wrong.

---

### Post by simon_7_1_8 on 2005-12-27
[QUOTE=sirlancelot]If, by connecting two cables from your router to a single computer you hope to acheive a faster connection, you would be wrong.[/QUOTE]

Well i believe that i would be correct in thinking that, because, if i connect my computer to my router through two network cards, then i would have a connection to the router which would be equivelent to 2x100mb/s. So how would my assumptions be inncorrect?

---

### Post by eoferror on 2005-12-28
What you're trying to do is called NIC Teaming. I've only done this in Redhat/Fedora and with Intel nic's. However you could give this a read: [http://www.howtoforge.com/nic_bonding]("http://www.howtoforge.com/nic_bonding")
Depending on the type of team you create you can have nic redundancy or increased speed.
[http://support.intel.com/support/network/sb/cs-009747.htm]("http://support.intel.com/support/network/sb/cs-009747.htm")

Good luck.....

Oh, BTW.... you need the bridge-utils for nic bridging however I've never been able to get the bridge to stick upon a reboot so you have to create a script to rebuild the bridge.

---

