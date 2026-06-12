---
title: "UFW firewall: /etc/sysctl.conf vs. /etc/ufw/sysctl.conf"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by cryptochrome242 on 2013-01-24
Hi,

usually you enable things like IP forwarding in /etc/sysctl.conf. Now I read through the UFW firewall documentation, and regarding to that, it has it's own sysctl.conf file in /etc/ufw.

Why is that? What happens if I enable UFW and have things configured in /etc/sysctl.conf? Will UFW overrule these settings with whatever is in /etc/ufw/sysctl.conf? Why two files for the same purpose?

Confused :confused:

12.10, by the way.

Thanks.

---

