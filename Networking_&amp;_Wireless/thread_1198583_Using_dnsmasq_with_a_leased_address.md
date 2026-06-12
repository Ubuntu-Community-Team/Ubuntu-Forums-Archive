---
title: "Using dnsmasq with a leased address"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by hrunting on 2009-06-27
I have a machine on my home network that serves as a caching DNS server when it is up.  It requests its address via DHCP from a wireless router.  The wireless router sends back my ISP's DNS servers with its response prepended with this machine's IP.

On boot, dnsmasq starts before the DHCP client runs.  When dnsmasq starts, resolv.conf is empty.  When the lease is assigned, resolv.conf is rewritten, and dnsmasq picks up on it, but one of the IPs is the machine's own IP.  Normally, dnsmasq will ignore resolv.conf entries for local IPs, but it appears that one of two things is happening:

a) dnsmasq doesn't get updated when IPs get added to a machine so it doesn't know the leased address is assigned to the machine

b) resolv.conf is getting edited before the lease has been configured on the interface

Either way, the solution is simple: restart dnsmasq.  Is there a simple way I can trigger this when the DHCP client configures a new IP address?  Right now, I have to do it by hand from the command line.

---

