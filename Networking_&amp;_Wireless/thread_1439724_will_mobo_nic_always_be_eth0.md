---
title: "will mobo nic always be eth0?"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by gmushial on 2010-03-26
I'm about to add pci ethernet card. Currently the mobo nic is eth0. When I add the new card will it by definition be eth1 (or will it become eth0 and the mobo nic become eth1)? The broader question is: how are the "eth's" numbered at boot time? If I were to add a 2nd pci nic, could I predict which would be eth1 and which would be eth2 (based on pci slot number??)? Is there somewhere to readup on this to get a broader understanding?
thanks - greg

---

### Post by Iowan on 2010-03-26
When I was using a Slackware based router (Freesco), the instructions said you couldn't predict which card would be assigned eth0, eth1, etc. Dunno if that's true for Debian-based systems or not...
I haven't tried it, but remember a thread that said (or at least suggested) you could "re-sequence" eth# by editing */etc/udev/rules.d/70-persistent-net.rules*

---

