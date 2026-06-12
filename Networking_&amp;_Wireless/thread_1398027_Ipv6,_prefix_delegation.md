---
title: "Ipv6, prefix delegation"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by yc2 on 2010-02-04
Hi,

I apologize if this is not the absolutely right forum for this question but, using Ubuntu and its forums for a long time, I think good help can really be found here.

I use Ubuntu server with router and forwarding now. It works fine and I have a general idea of how it works.

However, Ipv6 and prefix delegation is really a mystery to me. I think it is time to prepare oneself for that.

This is how Wikipedia explains it.
> In IPv6 networking, prefix delegation is used to assign a network address prefix to a user site, configuring the user's router with the prefix to be used for each LAN.

Ok, with a bit of imagination one can embrace the metaphor of that the old "switchboard with local lines" is being replaced by a "switchboard where we can dial the direct internal numbers from outside".

However, metaphors will not be enough when we must set up our routers.(We also have to buy new routers, don't we?)

Does anyone know a little more details about how these prefixes work?

Thanks.

---

### Post by SoftwareExplorer on 2011-08-08
(I know this thread is OLD. But I will still try to answer it).

Prefix delegation is done like IPv4 DHCP is done, except it give out a block of addresses instead of just one. 

At your ISP, a DHCPv6 server like Dibbler would run and be configured to give out addresses. Your router would run a DHCPv6 client and would ask for a block of addresses. When it got a block, it would take that block and give out individual addresses (or even smaller blocks if it was configured that way) to each computer on your LAN. 

To be honest, I don't know much about how you set up a computer/router to ask for a block of addresses on one interface and give them out on another. It's probably done using Dibbler.

As far as getting a new router, the answer is not necessarily. If you can put new enough software on the router that supports IPv6 you won't have to get a new one. Otherwise you might.

---

### Post by lemming465 on 2011-08-09
At the ISP level, IPv6 is like post-1993 IPv4: variable length prefixes are routed around using BGP advertisements.  IANA controls the upper 3 bits, the 5 RIR's control the next 9.  ISP's get something between a /13 (the US DOD) and a /32.  Anyone with an autonomous system number and a provider-independent IPv4 prefix can probably score a /32 network prefix in IPv6.  A typical business or large customer of an ISP should expect at /48.  What home users should expect is still in doubt, but /60 or bigger is likely in the long run.  What happens with the remaining subnet net bits (4-16) is up to the delegatee.  There is advice about what to do with them (start in the middle, use semantically significant small integers, aligned on 4-bit boundaries to ease reverse DNS), but no particular technical mechanisms to get from your ISP's /48 to your /64's.  You have great flexibility; in v6 it's like everyone was MIT and had their own legacy v4 class-A prefix.

There is a strong presumption in IPv6 that all subnets are /64 at the vlan, so that stateless autoconfiguration can use IEEE EUI-64 style identifiers as host parts.  Privacy addresses (62 random bits in the 64), CGA addresses (hash of public key), static or DHCPv6 are 4 other ways of assigning host parts.

DHCPv6 is not managed quite like DHCPv4; in IPv6 DHCP is controlled by a flag bit in the ICMPv6 router advertisements v6 routers emit.  Router advertisements contain mostly information about the on-link /64 prefixes and the gateway address of the router ( /128 ) to get off-link.  Since this week many clients (windows XP, Mac OS-X) don't do DHCPv6 queries, and as of February no consumer grade broadband or WiFi gear provided proper DHCPv6 responses, most production v6 networks currently use DHCPv4 for everything except the v6 address, which is composed from the RA prefix catenated with the clients choice of host part.

I'm not sure if that answers your questions.

---

### Post by yc2 on 2011-09-29
Thanks guys, I apologize for my very late reply, but your posts are very clarifying. Thanks.

---

