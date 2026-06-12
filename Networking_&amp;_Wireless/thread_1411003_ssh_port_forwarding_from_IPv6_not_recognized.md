---
title: "ssh port forwarding from IPv6 not recognized"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-02-19
A command like (single quotes used in the command):

```
ssh -L '[::1]:3128:127.0.0.1:3128' ...
```is getting an error message like:

**[FONT=Courier New]channel_setup_fwd_listener: getaddrinfo(::1): Address family for hostname not supported[/FONT]**

This is supposed to be an IP address, not a hostname, for the localhost in IPv6.  Anyone know what is wrong with this?  Addresses like this work OK in rsync.  I know I can use ip6-localhost as a hostname.  But right now I'm testing actual IP addresses in IPv6 to see what programs can or cannot handle it.

---

### Post by 2hot6ft2 on 2010-02-19
I think you'll find this helpful.

[Getting Around IPv6]("http://www.enterprisenetworkingplanet.com/netsp/article.php/3634596/Getting-Around-IPv6.htm")
> SSH connections are established like this, without the goofy escape guff:

$ ssh fe80::20a:e4ff:fe40:8bfd%eth1

You have to tell it the adapter to use

About half way down the page is ssh with ipv6

---

### Post by Skaperen on 2010-02-19
The interface index is only required on link-local addresses (those beginning with fe80) because they are never routed. Routable addresses, including unique-local, do not require it. Other applications that recognize IPv6 addresses do not require it.

And the issue is NOT with telling SSH which host to connect to. The issue is telling SSH which local interface to bind a listening to for port forwarding.

---

