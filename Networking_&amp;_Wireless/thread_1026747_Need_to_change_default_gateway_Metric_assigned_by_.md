---
title: "Need to change default gateway Metric assigned by DHCP"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Blackwood on 2008-12-31
Is there a way in the dhcpd.conf file (or somewhere else) to change the metric that is assigned for the default gateway on the clients?

I have dual nic'ed client machines and want to make sure that the default gw route added to the dhcp clients of my Ubuntu server has a higher metric than the other default gw route.  (I want to force it to use the other gw first.)

I haven't been able to find any setting in dhcpd.conf that will allow this.  How is the metric set on the client machine?

---

