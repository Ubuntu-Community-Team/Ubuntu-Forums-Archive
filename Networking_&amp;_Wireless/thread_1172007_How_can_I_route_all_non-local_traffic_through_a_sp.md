---
title: "How can I route all non-local traffic through a specific proxy server"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by System16 on 2009-05-28
I have a computer on a local network (10.X.X.X), and I need to route all non 10.X.X.X requests through a Smoothwall proxy server located at 10.100.1.1.  (My local IP address is 10.20.1.X if that matters.)  Everything works fine if I set the proxy in the global Network Proxy settings, but I'd like it to work for things like SSH, IRC, and various programs that don't allow you to set a proxy server.

I've searched high and low, but I don't really know what I'm looking for which made the process a lot more difficult!

---

### Post by superprash2003 on 2009-05-28
im not sure if this is what you mean [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by System16 on 2009-05-28
Perhaps, but I still need to be able to access local sevices.  How can I set that to be the default gateway for everything except addresses that start with 10.?

---

### Post by dstempfley on 2009-05-28
> **System16 said:**
> Perhaps, but I still need to be able to access local sevices.  How can I set that to be the default gateway for everything except addresses that start with 10.?

Is the 10.100.1.1 proxy your default router as well?  Are all your 10.x.x.x addresses on the same broadcast domain? i.e. is your network 10.x.x.x/255.0.0.0?  

The default gateway entry is a fallback entry.  This means that any traffic that doesn't have a specific route matched will be sent to the default gateway for processing.  If your 10.x.x.x network is a flat 8 bit network address then your interface setup should handle all of the networks in the 10.x.x.x space.  The interface initialisation will install a route for local network traffic to be handled by the ethernet interface.  The default gateway will catch the rest.

If you split the 10.x.x.x up across broadcast domains, i.e. 10.1.1.1/24, 10.20.100.1/24, etc, then you either need to setup a router to handle the different netblocks or setup a local static route for each netblock.  

For example:

   route add -net 10.1.1.0 netmask 255.255.255.0 dev eth0
   route add -net 10.20.100.0 netmask 255.255.255.0 dev eth0

I somehow doubt this is what you need, though.  Can you tell more about how the network is addressed?

---

