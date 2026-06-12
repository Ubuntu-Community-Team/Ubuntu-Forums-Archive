---
title: "DHCPv6 client - DHCPv6 reservation"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by Radvd on 2012-09-15
[B]HI,

How to configure DHCPv6 client on Linux Ubuntu 11.10 Desktop???
I got MS Server 2008 R2 DHCPv6, leases IPv6 address correctly to Windows users, but not to Linux users.
I installed "wide-dhcpv6-client" but nothing, does it need to be configured???
BTW: How can I get DUID and IAID of Linux user, and reserve IPv6 address on DHCPv6 service????

Pls, help!!!

Thanks in advance.[/B]

---

### Post by timothy-pickard on 2013-08-20
I didn't check to see how old your post was, but there wasn't a reply and I found your post early in my search for the same information. Here is what I've found so far. This page has some good information, both on installation of wide-dhcpv6 and configuration of both the client and server. I myself was only interested in the client side and found the method for creating a DUID in section 7. Follow the inputs in the gray section in your Ubuntu command line and you should have it. [http://www.rjsystems.nl/en/2100-dhcpv6-stateful-autocfg.php](http://www.rjsystems.nl/en/2100-dhcpv6-stateful-autocfg.php)

I haven't found how to find or make the IAID yet and if you are using a Windows Server for DHCPv6 you need that too. If I find that I'll either edit this post or make another reply.

---

