---
title: "Ubuntu network problem with Intel DG43NB mobo"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by nausicaavow on 2008-12-20
Hi all,
I am having a problem with successfully configuring the integrated gigabit ethernet (intel 82567v) on the DG43NB intel motherboard under Ubuntu 8.10.
The hardware (mac) address is detected, but I have been unable to even successfully ping any ip address.

I have tried dhcp configuration in /etc/network/interfaces as well as setting up a static address, with no luck.

ifconfig does not show RUNNING for eth0.

ifup etho sends out a DHCPDISCOVER to 255.255.255.255 (port 67), but no DHCPOFFER is received. Could this be a driver/configuration problem?
After ifup failes, it mentions /etc/resolv.conf does not exist (but i think this is only for name resolution anyway).

I use a linksys WRVS4400N router, and have DHCP enabled (with other clients connected).

Thanks for any help you can provide!

---

### Post by nausicaavow on 2008-12-21
Can anyone help? 
I know it is supported in the kernel, if i grep for e1000e in /lib/modules I can see the entry for device 10cb (82567V)

---

