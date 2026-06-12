---
title: "Asus NX1101 1gb Ethernet Adaptor issues (igp driver)"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by necro_gt4 on 2009-10-18
Hi,

I've just bought an Asus NX1101 network card that I want to use to have a direct link between my Ubunutu 9.04 desktop (samba file server) and my Windows XP HTPC.

Ubuntu detects the card as eth1 and I was able to succesfully configure it to talk to my HTPC via a crossover cable.

The problem is when streaming 720p video the card stops working after roughly 10 minutes. I read elsewhere that it could be the driver not working properly with auto negotiation so I turned that off but it still stops working.

I swapped the internal and new network card configs around so the NX1101 is used for the internet thinking it might be an issue talking to the XP machine. But it still does the same thing, the speed seems slow down to nothing and then come back to that of a VERY VERY slow modem then dies again...

Rstarting the network interfaces does bring it back up for awhile but I get this error...

/etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                       * if-up.d/mountnfs[eth1]: waiting for interface eth0 before doing NFS mounts
SIOCADDRT: No such process
Failed to bring up eth0.

If I swap eth1 back to the xp machine and eth0 to the internet it complains it cant bring up eth1, but it does work.

Any ideas?

---

