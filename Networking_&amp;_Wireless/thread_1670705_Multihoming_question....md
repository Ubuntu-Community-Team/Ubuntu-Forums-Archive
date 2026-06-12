---
title: "Multihoming question..."
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by zarac_ on 2011-01-19
We have three internet feeds that were previously connected via separate WRTs giving the LAN three distinct gateways. Two of the feeds have public IPs and some of these machines are providing Internet services via one of the public feeds by port forwarding through the WRTs. Switching Internet providers for any computer on the network was as easy as changing its gateway address. On the Macs, locations in the Apple menu were set up for each gateway. Even if the gateway for the machine was changed, request responses were sent via the request gateway. Load balancing is not an issue as each feed has specific uses, but the ability to switch feeds for individual machines is needed.

I set up a Ubuntu box with Gigabit Ethernet for the LAN and FastEthernet ports for the relatively slow feeds to use as a gateway router. I've been able to route traffic for normal operations out the various feeds based on source machine and destination IP, but have not figured out how to change the feed from an individual network machine. I originally thought I could use interface aliases to accomplish this, but have since learned route and iptables do not recognise interface aliases.

Adding ports to the Ubuntu box to put multiple physical ports on the LAN will require significant hardware changes. Before I do that, is there a way to set up separate LAN gateways for each feed with linux routing? Is there another solution that will allow users to switch feeds from individual machines?

---

