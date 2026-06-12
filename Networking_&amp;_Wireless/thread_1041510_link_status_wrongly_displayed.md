---
title: "link status wrongly displayed"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by hackeye on 2009-01-16
I'm facing a weird issue on Intrepid. I have 2 NICs on my machine and only one of them (eth0) is connected to the network.

[IMG]http://puneri.info/nics.jpg[/IMG]

However, ubuntu, for some weird reason, seems to think that a link is present on eth1:

```

root@linux:~# mii-tool 

eth0: negotiated 100baseTx-FD flow-control, link ok
eth1: link ok

root@linux:~# mii-tool -vv eth1

Using SIOCGMIIPHY=0x8947
eth1: link ok
  registers for MII PHY 32: 
    9000 780d 0000 0000 01e1 45e1 0000 0000
    0000 0000 0000 0000 0000 0000 0000 0000
    0000 0000 0000 0000 0000 0000 0000 0000
    0000 0000 0000 0000 0000 0000 0000 0000
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   software reset, autonegotiation enabled
  basic status: link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

root@linux:~# ifup eth1

Listening on LPF/eth1/00:e0:4c:b1:47:86
Sending on   LPF/eth1/00:e0:4c:b1:47:86
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Here is a bit more information about my system that may be useful:
```

root@linux:~# lspci | grep -i eth
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

root@linux:~# lsmod | grep -i 8139
8139too                35968  0 
8139cp                 31232  0 
mii                    14592  2 8139too,8139cp

root@linux:~# uname -a
Linux linux 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

```

Does anyone have any idea what's wrong here? Why is the network interface reporting a link when it's not there? Any help would be greatly appreciated.

---

### Post by cariboo on 2009-01-16
Why not take the nic you are not using out, that way Linux will not detect it, and you should have no problem.

Either that or give one of the nics, preferably the one you are not using a static ip address.
Jim

---

### Post by hackeye on 2009-01-20
> **cariboo907 said:**
> Why not take the nic you are not using out, that way Linux will not detect it, and you should have no problem.


Well, I can't really take the other NIC out, since it's a dual-boot system and the other NIC is used by the other OS.

> **cariboo907 said:**
> 
Either that or give one of the nics, preferably the one you are not using a static ip address.
Jim

Unfortunately, that is not an option. I'm inside a network which pretty much forces me to use DHCP, no matter which NIC i'm using.

Thank you for your suggestions anyway.

I have worked around this issue by putting a line:
```
/sbin/ifdown eth1
```
in /etc/rc.local

Then i get what looks like proper output from mii-tool:
```

root@sid-linux:~# mii-tool 
eth0: negotiated 100baseTx-FD flow-control, link ok
SIOCGMIIPHY on 'eth1' failed: Invalid argument

```

But the point i'm making is that shouldn't the lack of a cable connection be detected by the kernel? It gives me all sorts of network-related headaches, like dhclient trying to get an IP from the DHCP server and timing out, obviously), so i've to wait an extra few minutes at every network restart, apps binding to the non-existent interface and not working, etc. etc.

I feel this might be a bug 'cause i used to have CentOS on this box long ago and i never came across such a problem with it.

---

