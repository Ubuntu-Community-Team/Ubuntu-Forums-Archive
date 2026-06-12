---
title: "Ping 224.0.0.1"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by Sonofmoog on 2006-07-07
I learned on another forum that the command Ping 224.0.0.1 would report all the Linux PC's on my home network.  So I thought I'd give it a try.  I have three PC's multi-booting various OS'es as follows:

Left................ Center............Right
PCLOS............... XP................PCLOS
Ubuntu

My issue is with the box on the left.  When I ping 224.0.0.1 when it is running PCLOS, it finds itself (192.168.1.64) and the box on the right (192.168.1.100)  It also finds the IP of my router (192.168.1.254), but not the XP box.  This is exactly what should happen.

But, when I try ping 224.0.0.1 from either left or right with Ubuntu loaded, the IP of the box on the left is not reported.

Possibly this is a security issue, but more likely I think it's a problem with my SAMBA or NFS configuration.

So, my question is, when I ping the network, why doesn't Ubuntu answer, "Present, sir!"?

---

### Post by sal_veya on 2006-07-07
224.0.0.1 is the reserved multicast address for all systems of this subnet, and has nothing to do with any protocol other then IP. If your WinXP machine isn't responding it probably has something to do with the WinXP firewall, or other firewall installed on the box telling it to drop all unregistered multicast packets. It alternativley could be a broken multicast implementation on the WinXP Machine, but I doubt it.

**224.0.0.1  All Systems on this Subnet**

For more info see:
[http://www.cisco.com/univercd/cc/td/doc/cisintwk/ito_doc/ipmulti.htm](http://www.cisco.com/univercd/cc/td/doc/cisintwk/ito_doc/ipmulti.htm)

---

### Post by Sonofmoog on 2006-07-07
> **sal_veya said:**
> 224.0.0.1 is the reserved multicast address for all systems of this subnet, and has nothing to do with any protocol other then IP. If your WinXP machine isn't responding   [snip]

For more info see:
[http://www.cisco.com/univercd/cc/td/doc/cisintwk/ito_doc/ipmulti.htm](http://www.cisco.com/univercd/cc/td/doc/cisintwk/ito_doc/ipmulti.htm)

Thanks for the reply, and the link.

It's not the XP machine I'm concerned about; it's the machine running Ubuntu. It responds to the multicast broadcast when running PCLOS, but not when running Ubuntu.  I'd like to get that fixed, though in all honesty, it's not a big deal, since I can export both Linux systems under NFS, and I have bi-directional read-write access on all SAMBA shares from all machines ..

---

