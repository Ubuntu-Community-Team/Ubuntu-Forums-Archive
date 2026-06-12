---
title: "Using different gateways for different ports"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by MadJester on 2012-04-10
I need to configure a host to use a different gateway for all web traffic (ports 80,443).  The rest of the traffic should continue to route through the default gateway/router.  I need to route all web traffic to/from this host through an iptables system for nating and shaping etc.

The host system has a single public IP address, though I could potentially assign another, or an additional private IP.  The iptables gateway/router has multiple public addresses/interfaces.

Has anyone accomplished something of this nature?  I've been pondering different approaches, but I'm not sure which would work well.  Any suggestions?

---

### Post by MadJester on 2012-04-10
All systems are running Ubuntu 10.04 LTS server.

Thanks

---

### Post by roelforg on 2012-04-10
Outgoing or incoming?
incoming is easy with a few firewall rules (uwf or direct ip-tables?).
Outgoing's gonna be hard, but why?

---

### Post by MadJester on 2012-04-10
Outgoing.  Outgoing web connections need to be routed through an iptables server, and return traffic routed back through to the originating host.

It's not just one system.  We have a pool of systems that are each doing the iptables manipulation and traffic shaping individually.  I would like to route them all through one system that can handle this.

I have done this before based on destination network using iproute, but I'm not sure if it is possible to do it based on destination port.

---

