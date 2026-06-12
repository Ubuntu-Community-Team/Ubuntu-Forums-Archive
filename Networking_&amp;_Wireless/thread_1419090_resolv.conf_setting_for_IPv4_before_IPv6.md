---
title: "resolv.conf setting for IPv4 before IPv6"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-03-01
I have IPv6 running over my LAN and will be adding it to a private link to another LAN soon.  I do not have IPv6 to the whole internet at this time, and even when that does come, it will likely be a tunnel I don't want to put all the traffic to.

Right now, the resolver is behaving in an undesirable way.  It is querying AAAA records before an A record.  It's as if the "inet6" setting is on, even though it is not.

How can I turn this undesired behaviour off?  What I want for it to do is query A records not any later than it queries AAAA records.  If a host has an A record, I want to use that whether there is an AAAA record or not (because most hosts with this will be the internet and I cannot reach them with IPv6 at this time, and won't want to for a while even when I can).  If there is no A record but there is an AAAA record, THEN I do want to use the AAAA record (will be mostly internal hosts on my LAN for now).

I tried using options I speculated on that were not in the documentation: inet4, noinet6, -inet6 ... but no luck; it still queries AAAA records first.

This is on Ubuntu 9.10 and Ubuntu server 9.10.  Bind9 is at version 9.6.1.dfsg.P1-3ubuntu0.3.

---

### Post by Skaperen on 2010-03-02
This also happens when running the Ubuntu live CD. It does not happen in Fedora 12 or Slackware 12. I'm guessing it is at least an Ubuntu issue and maybe also Debian.

It will become more of an issue as the IPv6 transition grows. As more and more service hosts (e.g. web sites, FTP sites, etc) gain IPv6 connectivity and add AAAA records to their DNS zone, and more networks experiment with IPv6 before getting connectivity in IPv6, they will experience delayed or failed connections to sites that can and should be able to connect to.

The reverse problem is also real. As user networks become IPv6-only (because IPv4 space is exhausted), lookups to hosts that have both A and AAAA records, using the A-before-AAAA strategy, will have a similar failure.

Doing DNS lookup requests for the ANY record type is not an option. If a cache has only a subset of records for the requested host, only that subset will be given. It might seem that the solution would be a dual-type lookup type code that would request both A and AAAA records in one request. But that would have the effect of ignoring cache in cases where only one type had been cached, substantially increasing DNS loads.

The proper solution would be to make the resolver correctly obey local administrative and user policy by means of a configuration that specifies one of "A-only", "AAAA-only", "A-before-AAAA", and "AAAA-before-A". It would be a plus to also provide an environment variable standard for the resolver to check to override the configured policy on each process instance (in addition to any API features).

Currently the resolver has HALF (or less) of this in the form of an "inet6" option. Since there is no equivalent "inet4" option, a distribution changing the resolver to use "inet6" by default is BREAKAGE, because there is no longer administrative control.

---

### Post by idallen on 2012-07-25
This is exactly the question I want answered.
Try this:

[http://askubuntu.com/questions/32298/prefer-a-ipv4-dns-lookups-before-aaaaipv6-lookups](http://askubuntu.com/questions/32298/prefer-a-ipv4-dns-lookups-before-aaaaipv6-lookups)

---

### Post by wildmanne39 on 2012-07-25
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

