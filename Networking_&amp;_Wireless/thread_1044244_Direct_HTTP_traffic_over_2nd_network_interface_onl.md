---
title: "Direct HTTP traffic over 2nd network interface only?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Urinemachine on 2009-01-19
Hello all - I sit on a company network as part of the IT team.  More often than not I need to get to different sites for support that our firewall blocks (crackberry.com, etc).  I have to physically switch my ethernet cable here at my desk (I have an external connection for such purposes).  Is there a way I can throw a 2nd NIC in my PC running Ubuntu 8.10 and direct all HTTP or port 80 traffic over that NIC?  This way, I can get to the intranet and do all my domain admin stuff, but also get out to FTP sites to get software and websites that might be blocked that I need to access.

Any ideas?

---

### Post by Kebabman on 2009-01-19
Does it specifically have to apply to just port 80 traffic going outbound? ie would it be acceptable for you to point all traffic not destined for an internal address to the second NIC?

If that is acceptable then just create a routing table entry for everything internal to go through the NIC attached to the local network and a default route for everything to go via the second NIC and that will sort it.

---

### Post by Urinemachine on 2009-01-19
> **Kebabman said:**
> Does it specifically have to apply to just port 80 traffic going outbound? ie would it be acceptable for you to point all traffic not destined for an internal address to the second NIC?

If that is acceptable then just create a routing table entry for everything internal to go through the NIC attached to the local network and a default route for everything to go via the second NIC and that will sort it.

I think that would work - we do have an internal sharepoint server so that may make things sketchy.

What I do right now is run Ubuntu 8.10 on my desktop with a Terminal Server session into our Terminal Server and do all my Microsoft stuff there.  If I can maintain that but still get to the web over my external connection, that'd be the best.

Any examples of how to do this?

---

### Post by Kebabman on 2009-01-19
> **Urinemachine said:**
> I think that would work - we do have an internal sharepoint server so that may make things sketchy.

What I do right now is run Ubuntu 8.10 on my desktop with a Terminal Server session into our Terminal Server and do all my Microsoft stuff there.  If I can maintain that but still get to the web over my external connection, that'd be the best.

Any examples of how to do this?
I think the method I mentioned would still work fine. I presume the terminal services server is on an internal IP address? If so when you connect to it the route would still go over the internal NIC. All traffic (no matter what port) will go over the internal NIC when bound for an internal IP, everything else will not match the internal route and be forced over the default route which is via the external NIC.

Hope that makes sense and I'm not missing something from your question.

---

### Post by Urinemachine on 2009-01-19
> **Kebabman said:**
> I think the method I mentioned would still work fine. I presume the terminal services server is on an internal IP address? If so when you connect to it the route would still go over the internal NIC. All traffic (no matter what port) will go over the internal NIC when bound for an internal IP, everything else will not match the internal route and be forced over the default route which is via the external NIC.

Hope that makes sense and I'm not missing something from your question.

Thanks that sounds like what I want - now just, "how?"  hehe.  I am not very familiar with route tables and usually try not to mess with them.  I'll add an entry every now and then to hosts files but never messed with route tables.

---

### Post by Urinemachine on 2009-01-21
Bump - can someone explain how to do this?

---

### Post by Kebabman on 2009-01-21
To add the route for your local network you can do the following :

route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0

(Replace 192.168.0.0 with the network address of your local network and use an appropriate netmask. Also make sure you put in the NIC that is connected to your LAN after 'dev')

Then add a default gw using :

route add default gw xxx.xxx.xxx.xxx

You might need a 'dev eth1' after this, not quite sure. Give this a try and see if it routes your traffic appropriately.

---

### Post by Urinemachine on 2009-01-21
Thank you I will try this - how do I undo it should it not work?  I will be stranded :)

So if my internal ip is 167.21.233.x (and dhcp), and I want to route anything from 167.21.x.x to the internal, I would do:

route add -net 167.21.0.0 netmask 255.255.0.0 dev eth0  ???
and then

route add default gw 192.168.0.1   since my eth1 connection is 192.168.0.x (dhcp)?

---

