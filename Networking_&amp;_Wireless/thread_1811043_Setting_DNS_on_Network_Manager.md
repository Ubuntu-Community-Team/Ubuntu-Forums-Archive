---
title: "Setting DNS on Network Manager"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by manolomanolo on 2011-07-24
Hi to all.

I am trying to set a fix ip address with network manager since my router is not able to set it in order to make port forwarding for aMule.
I managed to set the IP address and also de primary/secondary DNS on network manager.

My question is: should I set the same DNS on bot the router and network manager?

More detail: my router has its own DNS's other than those of OpenDNS. At the moment, I left those DNS's on the router and set up the OpenDNS ones on network manager.
Is it correct or should I set the same DNS's on both the router and network manager? In this case, would it be a waste of time since there will be a sort of "double requesting" to the same DNS? Or one of the 2 DNS settings overrides the other one (for example, just the network manager DNS's are considered)?

Thanks for your time.
Regards.

Ubuntu Natty
Kernel 2.6.38-10-generic #46-Ubuntu SMP
Network Manager version 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1

---

### Post by jmoorse on 2011-07-24
> **manolomanolo said:**
> Hi to all.
My question is: should I set the same DNS on bot the router and network manager?


No, you dont need to.  The DNS 'server' on the router acts as a recursive fowarder to the servers you have specified in it's config.

If you specify DNS servers independently on clients connected to the router they will ignore the router's DNS server and go straight to OpenDNS.  Essentially you are cutting out the middleman :) 

That being said, there is no true penalty to using the DNS server on your router as a forwarder.  Perhaps a few extra ms of latency?

---

