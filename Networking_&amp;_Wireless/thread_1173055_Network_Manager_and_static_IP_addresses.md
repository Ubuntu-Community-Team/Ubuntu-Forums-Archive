---
title: "Network Manager and static IP addresses"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by nixIT on 2009-05-29
Hello all,

Using 8.10 Ubuntu here.

I am having problems assigning a static IP address with Network Manager.  I noticed when I installed Ubuntu we are not given an option to use DHCP or assign a static address, so I am using network manager.

Our firewall is configured to a couple IP addresses free range on the internet, mine is one of them.  However, when I installed 8.10, Network Manager gave me a DHCP address.  All is good, I can get on our corporate network and get out on the internet.  However, when I add a profile in Network Manager for my static IP address, this is where things go wonkers.  Things appear to work, but some applications, Evolution being the biggest pain, works intermittently, taking much longer to receive email, if it receives them at all, most times it just locks up.

when I switch back to "Auto eth0", which is DHCP, evolution seems to work properly.

What is the correct way to assign a static IP address?  I am running into this issue at home as well, and would rather not reconfigure my network resources, but instead assign a static IP address to my ubuntu box.

Any ideas?

--nixIT

---

