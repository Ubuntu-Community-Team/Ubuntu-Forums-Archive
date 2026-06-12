---
title: "dhclient3 started where?"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by fm1234 on 2006-02-26
Hi,

I still can't solve my DHCP problem, posted in this forum a week ago or so. Basically, I'm not able to have dhclient3 reusing the same IP from last session.

I would like to know how is dhclient3 started? 

I can't see it in /etc/init.d neither in inetd. I know where the conf file is, no problem (although the changes I've tried there didn't make any effect).

Also, if this is not the best forum, what would be the next place to look for help on dhclient3 or DHCP?

TIA,
Fernando

---

### Post by ape on 2006-02-26
dhclient3 is started via the ifup command as it reads through your /etc/network/interfaces file starts the desired interface that is configured with dhcp.

---

