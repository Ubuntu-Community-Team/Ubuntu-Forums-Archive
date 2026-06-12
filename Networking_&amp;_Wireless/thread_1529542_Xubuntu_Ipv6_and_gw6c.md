---
title: "Xubuntu Ipv6 and gw6c"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by wsteffen on 2010-07-12
I am using Xubuntu 10.04 and am trying to get the gw6c IPv6 
gateway client to working properly. I used the gw6c that aptget
provided, which installed every thing the start up script in init.d. After I customized the config (gw6c.conf) and rebooted I
got the following in the log:
Failed to connect to Gatewa6 broker.freenet6.net on port 3653.
Last status context is: Network connection

However if I start the script in init.d manually, it seems to run
correctly. I can then make an IPv6 connection to a site on an Ipv6 network.
Anyone gotten this to work and/or has any suggestions?

Thanks
W. Steffen

---

### Post by wsteffen on 2010-07-13
Update: I put a line in /etc/rc.local to start gw6c, and some times this work and some times not. From this I am guessing it is a timing issue. (the network connection is not yet ready when gw6c is started).

wsteffen

---

