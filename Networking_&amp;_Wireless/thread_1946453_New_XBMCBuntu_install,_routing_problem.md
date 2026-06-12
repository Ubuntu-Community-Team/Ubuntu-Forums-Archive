---
title: "New XBMCBuntu install, routing problem"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by Cuahtemoc on 2012-03-24
Hi

I just installed the latest build of XBMCBuntu and am having problems with the networking part of the UBUNTU setup.

I have the computer, an Acer Revo R3610 Intel Atom based PC connected via lan cable like so: Revo - Switch - Draytek 2820 modem/router

The Revo won't pickup an IP address via DHCP. Wanting to just get it to work, I set a manual IP using the following information:

auto      eth0
iface     eth0
broadcast 192.168.1.255
address   192.168.1.4
netmask   255.255.255.0
gateway   192.168.1.254

I can ping, and connect to via SMB, a file server located on my network at 192.168.1.2. I can also ping a windows server on 192.168.1.1. I cannot ping or get the webpage of the router on 192.168.1.254. I cannot ping google.com - either via the name or directly entering the IP. 

I have 9 other devices working on this network - a windows 7 desktop, windows server 2k8r2, esxi server, 2 solaris file servers, 2 laptops and 2 android phones and everything works perfectly.

I'd really appreciate any help you can give me.

---

### Post by logicslayer on 2012-03-29
Not to undermine your technical abilities, but are you sure that your router's IP address is 192.168.1.254? If you're able to ping and perform local activities but not access the internet, it sounds like a gateway issue.

---

### Post by lisanels47 on 2012-03-29
Verify on a working system the Route and IP setup.  
Windows: ipconfig /all

Not being able to ping outside the intranet, has to be a issue with the router and/or NAT on the router.  

And why wont the system pick up a dhcp setup?  Monitor your syslog or messages file for events when you connect a cable to the system. (tail -f /var/log/syslog)

Believe it or not, I have a similar issue on a NetGear fvs318n right now.  All computers work fine to the internet except the wired connection from my laptop... it's wireless works fine.  Same setup on all systems...

---

### Post by bitpalast on 2012-05-24
> **lisanels47 said:**
> I have a similar issue on a NetGear fvs318n right now.  All computers work fine to the internet except the wired connection from my laptop... it's wireless works fine.  Same setup on all systems...

We experience the same problem. Via wireless ports the router lets PCs access the Internet, but when using the wired ports it does not. After speaking with Netgear the router was exchanged against a new one: same problem persists. When we exchange the FVS318N against an FVS318v3, everything works fine (same IP configuration, same network, same DNS and so on).

Have you found a solution for the problem yet? It would be nice if you posted it here, because Netgear support does not have a solution for it yet.

---

