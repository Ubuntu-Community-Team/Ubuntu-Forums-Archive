---
title: "Wireless DHCP times out"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by bytbox on 2010-07-10
On a macbook5,4, running (ordinarily) Kubuntu 10.04 - connecting to any unsecured wireless network fails, and in syslog appears:

```
Jul 10 17:26:34 jagadai dhcpcd[6460]: eth1: dhcpcd 3.2.3 starting
Jul 10 17:26:34 jagadai dhcpcd[6460]: eth1: hardware address = aa:00:04:00:0a:04
Jul 10 17:26:34 jagadai dhcpcd[6460]: eth1: DUID = 00:01:00:01:13:b4:bb:00:aa:00:04:00:0a:04
Jul 10 17:26:34 jagadai dhcpcd[6460]: eth1: broadcasting for a lease
Jul 10 17:26:54 jagadai dhcpcd[6460]: eth1: timed out
Jul 10 17:26:54 jagadai dhcpcd[6460]: eth1: trying to use old lease in `/var/lib/dhcpcd/dhcpcd-eth1.info'
Jul 10 17:26:55 jagadai dhcpcd[6460]: eth1: using IPV4LL address 169.254.191.134
Jul 10 17:26:55 jagadai dhcpcd[6460]: eth1: adding IP address 169.254.191.134/16
Jul 10 17:26:55 jagadai dhcpcd.sh: interface eth1 has been configured with new IP=169.254.191.134
```

Or, trying dhclient:

```
Jul 10 17:46:55 jagadai dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jul 10 17:46:55 jagadai dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 10 17:46:57 jagadai dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jul 10 17:47:02 jagadai dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jul 10 17:47:11 jagadai dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jul 10 17:47:22 jagadai dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Jul 10 17:47:36 jagadai dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jul 10 17:47:45 jagadai dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jul 10 17:47:56 jagadai dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Jul 10 17:47:58 jagadai dhclient: No DHCPOFFERS received.
```

In all, I've tried three different kernels (2.6.31-14-generic, 2.6.31-21-generic, 2.6.32-22-generic), several dhcp clients (dhcpcd, dhcp-client3, bootp, maybe another), various network managers (wicd, the KDE, gnome, and XFCE network managers), with IPv6 enabled and disabled. It *was* working before - it stopped working after an upgrade (it was a large upgrade, and I don't remember anything about it, other than it was not the upgrade to 10.04 - it worked after I had 10.04).

Thanks for ... anything, really.

---

### Post by bytbox on 2010-07-11
Also, when I wireshark on the interface while trying to get a DHCP lease, I can see my requests and something about 'DECNet', but nothing that looks like an offer.

If I set up a DHCP server on the same computer (I haven't tried over ethernet yet, as I don't have another computer to set up a server on) I can get a lease without a problem.

Any ideas?

---

