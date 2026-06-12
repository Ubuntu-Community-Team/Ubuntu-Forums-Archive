---
title: "NetworkManager: DNS Domain Name Inconsitencies?"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by leuzi on 2009-04-12
Hi!

I recently discovered that Evolution fails to produce unique Message-Id headers for my e-mails. The FQDN part consists of the host name only. I tried to track down the problem and I think DNS domain names are not handled properly by NetworkManager.

My box is assigned a domain name via DHCP. This is working fine, as my */etc/resolv.conf* contains the correct *domain* and *search* lines. The */etc/hosts*, however, does not contain the domain name of the host in the *127.0.1.1* line. As a result, *gethostbyname(2)* returns an empty domain name (as does the *dnsdomainname* command; *getdomainname(2)* returns "(none)").

This doesn't feel right, because it means that I have to manually add the domain name to the */etc/hosts* file for DHCP clients.

Any comments or suggestions?

Thanks,
  Christoph

---

### Post by BigBaaadBob on 2009-10-05
This is definitely bogus and my scanning of the bug reports indicates it has been bogus for quite some time.  Does anyone know of a workaround?  Is there a specific bug for this?  I see the ancient bug #8980, but that got confused with non NetworkManager stuff...

---

### Post by BigBaaadBob on 2009-10-07
[https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/8980/comments/42](https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/8980/comments/42)

---

