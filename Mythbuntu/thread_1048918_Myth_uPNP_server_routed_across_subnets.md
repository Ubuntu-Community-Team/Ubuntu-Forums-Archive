---
title: "Myth uPNP server routed across subnets?"
date: 2009-01-24
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-01-24
MythTV 8.10: Myth front/backend is at 192.168.2.15. There are two subnets -- 192.168.2.x (wired) and 192.168.3.x (wireless) -- connected thru a Ubuntu 8.04 server. The server also runs OpenVPN (although I haven't tested whether machines on the OpenVPN subnet (10.8.0.x)). All machines on both subnets can open the MythTV default shares (Music, Recordings, Pictures....) but only those machines on the same subnet as the Myth backend see the uPNP media server.

I'd like to see it on the wireless subnet. The server runs Shorewall, but Policy allows all traffic between the two subnets.

Here's the routing table on the server:
```

:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
192.168.3.0     *               255.255.255.0   U     0      0        0 eth2
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
<extrn IP addr> *               255.255.255.0   U     0      0        0 eth0
default         L5000.VFTTP-03. 0.0.0.0         UG    100    0        0 eth0

```

What can I do to have the MythTV uPNP service show up on the wireless subnet?

Thanks,

DJ

---

