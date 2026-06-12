---
title: "DNS not working with Heartbeat and VIP"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by Modeverything on 2009-12-04
Hi everyone,

I have setup two Ubuntu servers, version 9.10 karmic, in a Heartbeat cluster using a Virtual IP Address, as noted here:
[https://wiki.ubuntu.com/UbuntuHighAvailabilityTeam/PacemakerHeartbeat](https://wiki.ubuntu.com/UbuntuHighAvailabilityTeam/PacemakerHeartbeat)

Well, the cluster, failover, and all works great, but the problem is my servers are not responding to DNS queries made against their virtual IP address.  They respond fine to queries against their actual IP, and I can ping their virtual IP and get a response, but the DNS service will not respond.  I have also tried connecting to them via SSH using by name, and while name resolution resolves their actual IP (not the virtual IP), they are not responding to SSH connections either; on any of their IP addresses.  I don't get a message back or anything, it just hangs.

Does anyone have any ideas on how to get these systems to respond on their virtual IP addresses?


Thanks in advance!

---

