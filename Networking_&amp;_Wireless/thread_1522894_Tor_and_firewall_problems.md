---
title: "Tor and firewall problems"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by coehorn on 2010-07-02
I set up Tor on a Kubuntu 10.04 box with a Netopia DSL router.  Everything looks pretty good but port forwarding has failed.  I have a hardware firewall on the router and I have no active software firewall as far as I can tell.

I enabled UPnP on the router and the TOR setup process said it auto-configured port forwarding.  

Unfortunately, the logs keep complaining:

------------

Directory Port Reachability Test Failed - Your relay's directory port is not reachable by other Tor clients. This can happen if you are behind a router or firewall that requires you to set up port forwarding. If 75.XXX.36.52:9030 is not your correct IP address and directory port, please check your relay's configuration.

Server Port Reachability Test Failed - Your relay's server port is not reachable by other Tor clients. This can happen if you are behind a router or firewall that requires you to set up port forwarding. If 75.XXX.36.52:9001 is not your correct IP address and server port, please check your relay's configuration.

----------------

BTW, 75.XXX.36.52 *is* my correct address.

I went into the router configuration and poked holes thru the firewall  at TCP ports 9001 and 9030.  Still no joy.  Is there any thing in Kubuntu that could be causing this or is it strictly a hardware firewall problem?

Sure appreciate any info......

---

