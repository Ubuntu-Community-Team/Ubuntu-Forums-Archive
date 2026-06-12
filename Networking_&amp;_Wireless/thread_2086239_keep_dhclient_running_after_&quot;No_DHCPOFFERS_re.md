---
title: "keep dhclient running after &quot;No DHCPOFFERS received&quot;"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by stroetgen on 2012-11-20
I use dhcp in /etc/network/interfaces:

[INDENT]auto eth0
iface eth0 inet dhcp
[/INDENT]
No network-manager installed.

This makes the dhclient run with option "-1":
[INDENT]dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -1 eth0
[/INDENT]
dhclient manpage:
       The  **-1**  flag  will  cause  dhclient to try once to get a lease.  If it        fails, dhclient exits with exit code two.When the dhcpd server is not reachable, the client exits after "No DHCPOFFERS received".

I want the dhclient keep running to get a new ip address when the dhcpd server is reachable again.

How can I configure this?

Thanks
Robert

---

