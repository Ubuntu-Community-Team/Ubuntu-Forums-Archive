---
title: "LAG instead of nic bonding"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by elvar on 2010-02-16
Hello,

I've run across a few threads in the archived forums regarding nic bonding. I could be wrong but I imagine most of the people that are looking at bonding are probably really wanting what they would get out of creating a LAG between their Ubuntu Server and a managed switch capable of LACP trunks. If you have two NICS on your ubuntu server and want 2gps throughput & failover check out the page on creating a LAG. Obviously this requires your switch to be compatible though.

[http://manpages.ubuntu.com/manpages/lucid/man4/trunk.4freebsd.html]("http://manpages.ubuntu.com/manpages/lucid/man4/trunk.4freebsd.html")

Maybe I'm wrong about the goals of those archived threads but hopefully this helps someone regardless. ;)


Regards,

---

### Post by elvar on 2010-02-16
Nevermind, I just realized that manpage was referring to FreeBSD only and not Ubuntu. Doh! Looks like 'mode=4 (802.3ad)' is what I was referring to.

[https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)

Sorry for the confusion.


Regards,

---

