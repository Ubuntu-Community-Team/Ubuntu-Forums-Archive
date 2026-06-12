---
title: "SOHO network DCHP, DNS"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by DrJohn999 on 2013-08-25
It's been a few years since I set up my SOHO network; now replacing the older server that provides DHCP & DNS and wondering if there are smaller-footprint ways to get this done instead of DHCP (isc-dhcp-server at this point) and BIND9. I've inserted a DDWRT capable router at the WAN side and am running a test subnet through it. The router currently provides DHCP for those devices that need it, outside DNS comes from Google 8's. Server is of course static. This gives me no local name resolution of the five or so devices and additional VMs that I'd like to have it for; in the previous configuration local and outside resolution and caching is provided by BIND9 on the server.

I can bring up DCHP3 & BIND9 on the new server, or install DD-WRT on the router and get it from there, or what? DNSMasq doesn't seem up to the task for local name resolution (or am I missing something); too many devices nor do I want to use a hosts file or equivalent to manually keep track. Plus I'll have a number of VM's coming and going on the local leg.

So, opinions / experience with DHPC and DNS configurations on a SOHO net with less than 7-10 devices?

Thanks!

---

### Post by papibe on 2013-08-25
Hi DrJohn999.

A few thoughts:
[LIST]
[*]The combo DHCPserver/Bind is not difficult that to set up, but if are not familiar with the syntax, it may take you some time to get it right.
[*]Dnsmasq provides both DHCP and DNS services, including adding the leases to the DNS for local resolution.
[*]I like DD-WRT a lot, but there are lots of inexpensive routers that can provide DHCP+DNS+local resolution.
[/LIST]
So in the end it is a matter of time versus budget. The simplest solution would be to buy a router. The next solution that would require less of your time would be setting up DNSmasq on a dedicated server. The ultimate solution, if you have the time and the drive to the proper documentation, would be to setup the famous combo.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Cheesemill on 2013-08-25
I've set up dnsmasq on several small networks and it provides DHCP and DNS with no issues.

What exactly are you wanting to do that you think dnsmasq can't handle?

---

### Post by DrJohn999 on 2013-08-25
> **Cheesemill said:**
> I've set up dnsmasq on several small networks and it provides DHCP and DNS with no issues.

What exactly are you wanting to do that you think dnsmasq can't handle?

Looking to know that either the router or DNSMasq can handle DHCP for wired and wireless, and local hostname resolution for samba shares, autofs, nfs, rsync, ssh, etc. Not having to configure DHSP/BIND on the server, just get the basics in a lower profile setup. Seems like yes, so I'll delve into it and see what's what, starting with the router. It's an ASUS RT-N66U, which is supported by DD-WRT, but maybe it's possible to use the ASUS default f/w for my simple needs.

---

