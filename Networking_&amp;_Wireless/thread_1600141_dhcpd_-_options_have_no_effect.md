---
title: "dhcpd - options have no effect?"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by Fatman_UK on 2010-10-18
```
allow unknown-clients;
default-lease-time 86400;
max-lease-time 172800;

subnet 10.23.31.0 netmask 255.255.255.0 {
        range 10.23.31.200 10.23.31.219;
        option broadcast-address 10.23.31.255;
        option domain-name-servers 10.23.31.10, 8.8.8.8;
        option netbios-name-servers 10.23.31.10;
        option domain-name "mydomain.local";
        option routers 10.23.31.2;
}
```

This works pretty well except option domain-name and option domain-name-servers seem to have no effect.

```
Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : home
   Description . . . . . . . . . . . : Atheros AR8152 PCI-E Fast Ethernet Controller
   Physical Address. . . . . . . . . : xx-xx-xx-83-57-62
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 10.23.31.103(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 18 October 2010 21:17:22
   Lease Expires . . . . . . . . . . : 19 October 2010 21:18:09
   Default Gateway . . . . . . . . . : 10.23.31.2
   DHCP Server . . . . . . . . . . . : 10.23.31.2
   DNS Servers . . . . . . . . . . . : 10.23.31.2
   NetBIOS over Tcpip. . . . . . . . : Enabled

```

Any ideas? TiA.

[The server is Ubuntu 10.04 32-bit. The client is Windows 7 Ultimate 64-bit.]

---

