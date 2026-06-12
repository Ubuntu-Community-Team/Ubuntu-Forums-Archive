---
title: "Using local hostname with local domain to access local network"
date: 2006-01-07
forum: Networking &amp; Wireless
---

### Post by adamonduty on 2006-01-07
Hello,

I've been trying to get my breezy server to have a hostname on my local domain along with every other machine. I'm using a wrt54g with sveasoft firmware to run local dns and dhcpd is configured to use myname.net . So each of the machines on my network is somehost.myname.net . The windows machines just use their computer name and my SUSE box does likewise. But ubuntu won't fork out its hostname to dhcpd on the router. This happens on both my server and wireless laptop running ubuntu. I'm able to ping my desktop at ultimator.myname.net (or even simply ping ultimator) but I can't ping isaiah (my server). 

I've temporarily worked around the problem by using static dhcp (and force dhcpd to bind isaiah with its IP), but I'd rather just get ubuntu to work properly. 

Any suggestions, hints, solutions?

---

