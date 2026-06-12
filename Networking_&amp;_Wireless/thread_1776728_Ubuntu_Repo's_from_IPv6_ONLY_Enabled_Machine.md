---
title: "Ubuntu Repo's from IPv6 ONLY Enabled Machine"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by NicholiS on 2011-06-06
Cannot resolve addresses for any of the Ubuntu repo's in order to run apt-get.

The "machine" is actually a linux-vserver (running Lucid Lynx) with ONLY an IPv6 address. As far as I am aware everything is setup correctly in order to use IPv6, but of course that's why I am here. I can resolve other IPv6 enabled domains (like Google's), and can ssh the server itself over its IPv6 address.

Are the Ubuntu repo's available over straight IPv6? Do I need to use a particular nameserver in order to resolve Ubuntu's repo's? I am currently using he.net's nameserver if that may have any bearing on the issue at all. I am sort of at a loss of how to continue troubleshooting this problem.

Once again this machine has only an IPv6 address, and I am _not_ tunneling over IPv4.

---

### Post by lemming465 on 2011-06-07
If I run "host ..." for any of the various servers listed in /etc/apt/sources.list or the like, I don't get back any v6 addresses.  I don't think Canonical is particularly v6-enabled yet.  You can find occasional mirrors which are dual-stacked.

The experience of the "ipv6 hour" at NANOG-42 (February 2008, San Jose, CA, USA) remains pertinent: for maximum compatibility, be dual stack, not IPv6-only.  IPv6 only is still very bleeding edge, and will be until around 2015 or so.

---

### Post by NicholiS on 2011-06-08
Thanks for the response. I wasn't quite sure if I was supposed to be able to resolve them over just IPv6, got some misinformation from other people.

---

