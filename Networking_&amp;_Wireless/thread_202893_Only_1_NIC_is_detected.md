---
title: "Only 1 NIC is detected"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by ashrack on 2006-06-24
I have 2 NICs in the PC but only one NIC is detected. Hers the 'lspci -v' info:
```
0000:00:08.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
        Subsystem: Unknown device 3030:5032
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e400 [size=256]
        Memory at ea001000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e8000000 [disabled] [size=256K]
        Capabilities: [50] Power Management version 2

0000:00:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
        Subsystem: Unknown device 3030:5032
        Flags: bus master, medium devsel, latency 64, IRQ 3
        I/O ports at e800 [size=256]
        Memory at ea000000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e9000000 [disabled] [size=256K]
        Capabilities: [50] Power Management version 1

```

ifconfig info:
```
eth1      Link encap:Ethernet  HWaddr 00:08:A1:0E:0A:F9
          inet6 addr: fe80::208:a1ff:fe0e:af9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:770880 (752.8 KiB)  TX bytes:213644 (208.6 KiB)
          Interrupt:3 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2368 (2.3 KiB)  TX bytes:2368 (2.3 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:193.77.242.136  P-t-P:213.250.19.90  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:736274 (719.0 KiB)  TX bytes:179741 (175.5 KiB)

```

mousepad /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth1
    iface eth1 inet manual

    pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf

```

---

