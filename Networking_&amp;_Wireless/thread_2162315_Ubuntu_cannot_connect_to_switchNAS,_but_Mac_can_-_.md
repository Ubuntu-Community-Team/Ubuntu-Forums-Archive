---
title: "Ubuntu cannot connect to switch/NAS, but Mac can - what happens when no DHCP server?"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by chowdy155 on 2013-07-14
Hi,

Have a mid-2010 Macbook Pro that I dual boot with Mac (OS 10.8.4) and Ubuntu (12.04).  Via ethernet cable, Mac can connect to a NetGear FS105 switch which is also connected to a NAS no problem.  However, Ubuntu cannot establish a connection.  But if I plug the switch into a router then Ubuntu can connect to the switch/NAS no problem.  The switch and NAS do not have a DHCP server, while of course the router does.

So the two OSs are using the same exact hardware yet Mac seems to be able to connect to the switch/NAS with no DHCP server present, yet Ubuntu does not.  I assume Mac has some default where if no DHCP server is present then it automatically sets an IP address, while it seems Ubuntu by default does not do this.  I have not been able to find much information concerning these issues.  Can anyone confirm/deny this?  What happens in Ubuntu when no DHCP server is present but it is connected to a network?  Most important, how can I change Ubuntu to make it behave like Mac (it would be very advantageous to be able to connect to the switch/NAS without having to use the router!)?

Thanks!

---

### Post by steeldriver on 2013-07-14
Sounds like either the Mac has a static IP defined somewhere, or both the Mac and the NAS are falling back to link-local addressing --> [https://en.wikipedia.org/wiki/Link-local_address](https://en.wikipedia.org/wiki/Link-local_address)

If the IP address it is showing under the Mac OS is 169.254.x.x then it is link-local and you can try setting Ubuntu's network-manager to use link-local as well via the connection applet (Edit connections... select the connection by name --> IPv4 Properties tab --> change the 'Method' dropdown to 'Link local only'). If it's got a static address under Mac OS then you can set that in the same place (set method to 'Manual' and fill in suitable address and netmask fields).

---

### Post by chowdy155 on 2013-07-14
Yes, turns out it was link-local!  Now everything works great!  Thanks so much!

---

