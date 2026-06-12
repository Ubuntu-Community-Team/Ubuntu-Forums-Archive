---
title: "Setting up IPV6 private network?"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by hellmet on 2010-03-08
Pardon me, but IPv6 is terribly confusing as of now. I wish to setup an Ubuntu machine with IPV6 to talk to a private IPv4 network. I do not need these machines to connect to the Internet. However, I read that there is no concept of a private IPv6 network. 

So, how would I assign this machine an IPv6 address and (IPv4) DNS and (IPv4) Gateway IPs. Do I use a tunnel? If so, how do I assign it an IPv6 address? How can I configure it for DHCP IPv6 assignment? Does it need a separate IPv6 DHCP server? Sorry, lots of questions. Any help (and/or tutorials) in the right direction would be extremely appreciated.
Thanks!

---

### Post by Skaperen on 2010-03-08
Some people will deny that a private IPv6 network exists.  Others will argue it's not needed.  But it does exist.  See RFC4193.

[http://tools.ietf.org/html/rfc4193](http://tools.ietf.org/html/rfc4193)

You do not need any tunnels for an IPv6 network over networking components that do not care about the IP protocol used, or understand enough IPv6 to pass it through.  You may run into a security issue where firewalls you expect to block things by deep packet inspection are not doing so for IPv6.

You can configure interfaces statically with the "ifconfig" or "ip" commands.  With "ifconfig" you do not use alias interface names in IPv6.  Instead, use a command like "ifconfig eth0 add fc00::123/48" to add an IP to eth0.  You can also do this through /etc/network/interfaces but I did not memorize how that is done.  Interfaces can have both IPv4 and IPv6 addresses ... and quite many of them if you wish.

Where you will need tunnels is where you need to carry IPv6 traffic over paths having no IPv6 routing capability.  Unmanaged ethernet switches, and most managed ethernet switches, should carry IPv6 around the LAN just fine.  Layer 3 switching might be a problem for those that don't implement IPv6.

---

