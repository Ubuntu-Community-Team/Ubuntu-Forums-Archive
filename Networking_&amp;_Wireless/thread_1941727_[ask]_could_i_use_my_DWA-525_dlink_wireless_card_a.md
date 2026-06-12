---
title: "[ask] could i use my DWA-525 dlink wireless card as access point?"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by metabee on 2012-03-16
I would like to using my PC as acces point.
My operating system is Ubuntu 10.4 server installed on pentium 4 with 256 MB of RAM.

this my iwconfig
```
root@ubuntu:/# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```this is my ifconfig
```
root@ubuntu:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:c5:a9:87
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fec5:a987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20024966 (20.0 MB)  TX bytes:1404910 (1.4 MB)
          Interrupt:5 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0       Link encap:Ethernet  HWaddr 34:08:04:9b:13:dd
          inet addr:192.168.2.102  Bcast:192.168.2.0  Mask:255.255.255.0
          inet6 addr: fe80::3608:4ff:fe9b:13dd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:31047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3323254 (3.3 MB)  TX bytes:0 (0.0 B)
          Interrupt:10
```this is my lshw -C network
```
root@ubuntu:/# lshw -C network
  *-network:0 DISABLED
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth1
       version: 74
       serial: 00:01:02:87:07:10
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: irq:5 ioport:bc00(size=128) memory:fe5ffc00-fe5ffc7f memory:10000000-1001ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: ra0
       version: 00
       serial: 34:08:04:9b:13:dd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0-alpha20100128 ip=192.168.2.102 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:10 memory:fe5e0000-fe5effff
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:0b:6a:c5:a9:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.250 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:5 ioport:b800(size=256) memory:fe5ff800-fe5ff8ff
```I hope someone can help me on this issue.
thanks for the explanation...:p

---

