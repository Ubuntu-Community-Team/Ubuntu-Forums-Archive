---
title: "wired network suddenly unreachable from any linux, not win"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by mjhess on 2011-04-10
**Hello All:**

I have all of a sudden lost access to my wired network from my ubuntu machines. Booting to windows XP, it runs just fine.

I came cross several messages point to the "missing eth0" entries in /etc/network/interfaces and so added
[INDENT]auto eth0
iface eth0 inet dhcp
[/INDENT]and restarted networking through
[INDENT]sudo /etc/init.d/networking restart
[/INDENT]I get a
Listening on LPF/eth0/00:12 ...
Sending on LPF/eth0/00: ...
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interface 6
and so on till ...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Now, if I plug a ubuntu netbook into the same cable, I have the same problem, wireless is fine, but no wired access.
If I plug in a cable that goes to another wireless router, same thing,
but the netbook can see the wireless router over wireless so I'm assuming this is not a cable issue.

I could understand two machines failing if something on the router (Linksys WRK54G) changed (how?), but how would I fix this so that both ubuntu machines can see the wired part of it again?

Router Setting:
Local Gateway: 192.168.1.1
Subnet Mask: 255.255.255.0
DHCP Range is set from 100 to 149
and the table shows seven connected devices.

Maybe it's not the router.

Thanks for any pointers,

**Mike**

---

