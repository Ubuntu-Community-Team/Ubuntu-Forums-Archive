---
title: "DHCP Server Keeps Changing DNS Server option to localhost"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by TaoJoannes on 2009-09-11
Howdy all, 

I've got the latest Debian distro installed on a Dell PC and I'm having some odd trouble with dhcpd3

uname -a
Linux beagle 2.6.26-2-686 #1 SMP Wed Aug 19 06:06:52 UTC 2009 i686 GNU/Linux

I installed the GADMIN tools to manage my DHCP, etc, and was originally going to set up a forward-caching DNS server, but the GUI doesn't have the option yet, so I decided to table it. 

However, it looks like my system really, really wants to act like a caching server. It's resolving with localhost as the dns server.

I should mention that my internet interface has a DHCP assigned address and DNS servers, and if I assign those DNS servers manually, then manually release and renew the lease, the client will pull the updated servers. But a little while later it just throws it and starts resolving against localhost. Outside of this behavior, the firewall and NAT is working perfectly (well, except that Firestarter just seems to dissapear every once in a while, and doesn't seem to want to start on boot, but one thing at a time)

I check the config on the server, and the correct servers are no longer listed in dhcpd.conf.

If I manually edit dhcpd.conf, it doesn't seem to take, but if I change it in the GUI, it will work for a little while.

I'm guessing there's some daemon that is going around behind me and "fixing" things, just like it seems the network interfaces are wont to do, I'm just at my wits end trying to figure out how to get it to stop.

Any insight would be greatly appreciated, as I'm tired of giving up MY machine so my wife can play Bejeweled Blitz on facebook.

---

