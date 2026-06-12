---
title: "How to setup NAT?"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Ugluk on 2009-04-28
How can I setup my machine as a NAT between DHCP WAN segment and static IP LAN segment?

---

### Post by Iowan on 2009-04-28
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page contains a section:> The ipmasq daemon does NAT routing so you don't have to configure iptables. The following directions are incomplete and should not be considered a full description of what needs to be done to configure ipmasq.

sudo aptitude install ipmasq

---

