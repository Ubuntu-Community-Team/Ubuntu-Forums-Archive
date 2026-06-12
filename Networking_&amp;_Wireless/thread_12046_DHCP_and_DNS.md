---
title: "DHCP and DNS"
date: 2005-01-21
forum: Networking &amp; Wireless
---

### Post by Swad on 2005-01-21
For some reason, my Ubuntu computers are not reporting a FQDN to the DHCP server when getting a lease.  This is somewhat problematic as it thus makes it impossible to access this computer remotely via it's hostname / FQDN.  The only possible way is via it's IP address that it got from the DHCP lease.  I do know that the DHCP server processes FQDNs just fine for other windows machines on our network, but the FQDN for the Ubuntu machines is empty when browing the entries on the DHCP server.

Long story short--how does linux report that information to the DHCP server when getting a lease so it's recorded on the DHCP server, and thus replicated to DNS for other computers to resolve the name?

---

### Post by vairoj on 2007-02-12
I'm having the same problem right now. Did you manage to solve the problem?

---

### Post by Abhi Kalyan on 2007-03-15
dhcp3-server and BIND9 have to authenticate to each other using a MD5 key. This is a file.
Unles this happens i think the anmes do not get updated.
Also check the lease times and update intervals.
All the best
check this link out
[http://ubuntuforums.org/showthread.php?t=267974&highlight=DNS](http://ubuntuforums.org/showthread.php?t=267974&highlight=DNS)

---

