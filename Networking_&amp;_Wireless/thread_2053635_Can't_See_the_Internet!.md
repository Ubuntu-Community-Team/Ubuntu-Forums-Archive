---
title: "Can't See the Internet!"
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by steveferson on 2012-09-05
Hi,

I'm running Lubuntu 12.04 on a HP Proliant Microserver, but I don't think this is specifically a Linux issue.

My server can't see the internet. At all!  

I CAN
* Ping/access local network resources from the server
* Connect to the router (Virgin Superhub) web admin interface
* Access the server locally (the server has a reserved DHCP lease at IP 192.x.x.50)
* SSH over the internet INTO the server

I CAN'T
* Ping out to the internet (by name OR IP)
* access websites
* perform upgrades

I'm writing from a laptop, connected wirelessly to the same network, so there isn't a network-wide internet connectivity issue.  This laptop is also able to Remote Desktop or SSH into the box.

Anyone got any thoughts? This was fine very recently when I reinstalled Lubuntu.  The only thing I can think of was that I did a hardware reset of my router recently, but I can't think why this would have changed anything that should cause this!

---

### Post by steveferson on 2012-09-05
Never mind - turns out I had screwed up the networking in the router config.  I'd added a MAC filter which, since the default is to allow everything, blocked traffic from my server's IP.

*hangs head*

---

