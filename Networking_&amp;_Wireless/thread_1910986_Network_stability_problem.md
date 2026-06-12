---
title: "Network stability problem"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by kiolul on 2012-01-18
Hello,

After numerous search on the web, i post a thread on this forum.
First my configuration: VMWare's virtual machine with Ubuntu Server 11.10 64bits (network card intel E1000).
Rules: nagios, PnP4Nagios, Apache web server and of course lots of dependencies.
I check machines on my company network with routing (this task is done by an unique router wich is define as the default gateway) between various networks.
It works, but sometimes i lost a host check.
The symptoms: i can ping this host but no traceroute, other hosts works fine. It's like i lost the route to a complete subnetwork.
The temporary solution find: reboot the server and all works again. Just a networking restart is not enough.

Is it possible that a "routing table" will be full and the reboot flush it?
Any ideas/solutions

Thank you.
Regards.

---

