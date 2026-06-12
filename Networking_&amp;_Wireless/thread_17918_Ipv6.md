---
title: "Ipv6"
date: 2005-03-03
forum: Networking &amp; Wireless
---

### Post by awstott on 2005-03-03
The other night I was having hardware issues with one of my hard drives in another box, so I thought i'd take it out and try it in my ubuntu box.  After I tested the drive i put the ubuntu box back to the way it was and booted it up.  When it attempts to bring up eth0 it hangs.  I have DHCP active on my linksys router (it was orignaly getting an IP from my ISP), so I thought that might be the problem.  I switched it over to my lan to test this.  When I look at the ifconfig, it's an IPV6 address.  It seems it's not accepting the IP offered by the DHCP server.  I do a /etc/init.d/networking restart and it still stays the same.   Any idea whats going on?

Thanks in advance for any suggestions,

Andrew

---

### Post by lucan on 2005-03-03
hi,
could you tell me what is IPv4 and IPv6? what's the different between them?

---

### Post by bored2k on 2005-03-03
[QUOTE=lucan]hi,
could you tell me what is IPv4 and IPv6? what's the different between them?[/QUOTE]


Here's what good ol` wiki had 2 say 
[IPv4 Wiki](http://en.wikipedia.org/wiki/IPv4)  #-o 
[IPv6 Wiki](http://en.wikipedia.org/wiki/IPv6)  =D>

---

### Post by awstott on 2005-03-08
Well genius me found the problem.  When i was messign around with the hardware the other day somehow the bios got reset.  I have an onboard NIC so that became enabled.   This NIC was assigned eth0, and because it wasn't plugged in, ubnuntu assigned the IPv6 address.  Once I realized this and disabled it, everything worked like a charm

---

### Post by bored2k on 2005-03-08
[QUOTE=awstott]Well genius me found the problem.  When i was messign around with the hardware the other day somehow the bios got reset.  I have an onboard NIC so that became enabled.   This NIC was assigned eth0, and because it wasn't plugged in, ubnuntu assigned the IPv6 address.  Once I realized this and disabled it, everything worked like a charm[/QUOTE]
 Wow 5 days after the 1st post u found a solution ? those days had to be hard ....

---

