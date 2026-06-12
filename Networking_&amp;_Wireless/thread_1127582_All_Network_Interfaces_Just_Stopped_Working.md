---
title: "All Network Interfaces Just Stopped Working"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by libertydog on 2009-04-16
Alright this is weird.

I installed Ubuntu 8.10 x64 on my HP DV4 Laptop last week.  Both the Broadcom wireless and Realtek 10/100 were detected fine and I have been running fine ever since. 

Today when I booted up I got *no* network connectivity.

I have not installed any updates.

I am using the NetworkManager and it has been working fine in the past traveling between two different wireless sites.  

The wired network was also working fine as I have plugged in at work to transfer some large files at least four times.

Now, the wireless network (eth0) just won't see any networks and the wired shows eth0: "down" no matter what although manually assigning an address allows it to ping itself so it must "see" a link at some level, and the switch sees the link, and ifconfig shows it "UP" but the network gateway can't be pinged and it always shows "down" in the messages log.

I have attached some system info and diagnostics below.

Soooo weird.  Anyone have any ideas?

-Vin

uname -r
2.6.27-7-generic

root@libertydog:~# lspci | grep Ethernet
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

root@libertydog:~# lspci | grep Network
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

root@libertydog:~# dmesg | grep eth0
[    6.237559] eth0: RTL8169 at 0xffffc2000064c000, 00:23:5a:39:2d:89,
XID 24c00000 IRQ 2299
[   20.327419] r8169: eth0: link down
[   95.273745] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  542.149043] r8169: eth0: link down
[  551.944156] r8169: eth0: link down

root@libertydog:~# dmesg | grep eth1
[  108.179214] bridge-eth1: is a Wireless Adapter
[  108.179277] bridge-eth1: up
[  108.183055] bridge-eth1: attached
[  113.168840] bridge-eth1: disabling the bridge
[  113.196556] bridge-eth1: down
[  113.199570] bridge-eth1: detached
[  118.388082] eth1: no IPv6 routers present

root@libertydog:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:5a:39:2d:89
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:135 errors:0 dropped:15577187602 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:11505 (11.5 KB)  TX bytes:0 (0.0 B)
         Interrupt:251 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:21:00:c0:ba:e9
         inet6 addr: fe80::221:ff:fec0:bae9/64 Scope:Link
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:18

root@libertydog:~# ifconfig eth0 10.0.0.2 netmask 255.255.255.0
root@libertydog:~# ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:23:5a:39:2d:89
         inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:138 errors:0 dropped:20774457724 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:11685 (11.6 KB)  TX bytes:0 (0.0 B)
         Interrupt:251 Base address:0xc000

root@libertydog:~# ping 10.0.0.2

PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.105 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.044 ms
^C
--- 10.0.0.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms 
rtt min/avg/max/mdev = 0.044/0.074/0.105/0.031 ms

root@libertydog:~# ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 10.0.0.2 icmp seq=1 Destination Host Unreachable
From 10.0.0.2 icmp seq=2 Destination Host Unreachable
From 10.0.0.2 icmp seq=3 Destination Host Unreachable
^C
--- 10.0.0.1 ping statistics ---

4 packets transmitted, 0 received, 100% packet loss, time 0ms

---

