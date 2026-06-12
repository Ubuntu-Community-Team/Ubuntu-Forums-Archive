---
title: "Bind9 (9.4.2) in Ubuntu 9.1"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by rievax on 2009-12-14
Hello,
 
Anybody here knows Bind works? I have a working configuration with a Bind hosting secondary zones. No problem with my configuration, everything is working except that if have a none existing zone defined in my "named.conf.local" bind does not load.
 
For example, if I have 10 secondary zones defined in /etc/bin/named.conf.local but one of them does not exist in the primary (master) DNS, syslog shows:
 
Dec 14 12:06:49 servername named[26357]: zone MyBadZone.com/IN: refresh: unexpected rcode (SERVFAIL) from master 192.168.2.51#53 (source 0.0.0.0#0)
 
... which is an OK message, but Bind will not start unless I take care of this MyBadZone.com.
 
Is this by design? Can we tell Bind to start even if it doesn't find the zone in the Primary (master) server?
 
Thank you!
 
X.

---

