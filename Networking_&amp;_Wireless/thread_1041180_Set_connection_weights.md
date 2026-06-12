---
title: "Set connection weights?"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by silverbullet007 on 2009-01-16
Is there a way to set either connection profiles or set weights on a per interface basis?  For example.. when the ethernet post is being used I'd like the wireless not to associate.. or maybe when docked I'd like the wireless not to connect automagically.. 

Is there a way to do this?

---

### Post by silverbullet007 on 2009-01-16
Bump

---

### Post by silverbullet007 on 2009-01-20
Bump

---

### Post by silverbullet007 on 2009-01-21
I cannot believe that no one knows anything about this or at the least.. no one would want this if it doesnt exist.  I upgraded from Hardy to Intrepid and without turning off the "wireless" switch on the side of my T43 and thereby also shutting down Bluetooth which I'd rather not do.  I can't find anything in ubuntu to do this.

---

### Post by Kebabman on 2009-01-21
ifconfig <wireless device> down?

---

### Post by silverbullet007 on 2009-01-22
Manually... everytime? C'mon.  Not a good way to win non-experienced users over to Linux.  Seriously I might not have explained it well enough.  Intrepid on my T43... without a dock and plugged into the LAN when it boots up it wants to use wireless over the already present hard-wire.  Unless it's just really wanting an actual dock.. I would think that the wlan shouldn't take priority over a faster hard lined connection.

---

### Post by Kebabman on 2009-01-22
I usually just go to network-admin and disable my wireless connection or do what I stated above. Unfortunately the network that received a DHCP reply most recently will take priority as the default route received in the reply will be the one that gets added to the routing table.

---

