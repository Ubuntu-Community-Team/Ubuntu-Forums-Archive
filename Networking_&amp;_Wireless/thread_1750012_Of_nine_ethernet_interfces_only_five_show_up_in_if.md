---
title: "Of nine ethernet interfces only five show up in ifconfig, can you help?"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by martinrenshaw on 2011-05-05
I have build a xubuntu 64bit PC so I can load gns3 the Cisco router emulator, in the PC I have installed two quad ethernet cards, their is also a gigabit nic onboard.
 
```
mrenshaw@gns3-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:90:75:58
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe90:7558/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:334106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:213616410 (213.6 MB)  TX bytes:20257043 (20.2 MB)
          Interrupt:44 Base address:0x8000
eth1      Link encap:Ethernet  HWaddr 00:e0:b6:03:38:3c
          inet6 addr: fe80::2e0:b6ff:fe03:383c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60 (60.0 B)  TX bytes:6066 (6.0 KB)
eth2      Link encap:Ethernet  HWaddr 00:e0:b6:03:38:3b
          inet6 addr: fe80::2e0:b6ff:fe03:383b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5488 (5.4 KB)
eth3      Link encap:Ethernet  HWaddr 00:e0:b6:03:38:3a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
eth4      Link encap:Ethernet  HWaddr 00:e0:b6:03:38:39
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:256767 (256.7 KB)  TX bytes:256767 (256.7 KB)

```
 
If I do an mii-tool this is what I get
 
```
mrenshaw@gns3-ubuntu:~$ sudo mii-tool
[sudo] password for mrenshaw:
eth0: negotiated 100baseTx-FD flow-control, link ok
eth1: negotiated 1000baseT-HD flow-control, link ok
eth2: negotiated 1000baseT-HD flow-control, link ok
eth3: no link
eth4: no link
eth5: negotiated 1000baseT-HD flow-control, link ok
eth6: negotiated 1000baseT-HD flow-control, link ok
eth7: no link

```
 
and from dmesg
 
```
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth1
[    2.165155] e100 0000:06:00.0: eth1: addr 0xfceff000, irq 16, MAC addr 00:e0:b6:03:38:3c
[   17.582565] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6419.980269] e100 0000:06:00.0: eth1: NIC Link is Up 100 Mbps Full Duplex
[ 6419.981222] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6430.470005] eth1: no IPv6 routers present
[ 6475.980313] e100 0000:06:00.0: eth1: NIC Link is Down
[ 6477.980268] e100 0000:06:00.0: eth1: NIC Link is Up 100 Mbps Full Duplex
[ 6509.980311] e100 0000:06:00.0: eth1: NIC Link is Down
[ 6525.980266] e100 0000:06:00.0: eth1: NIC Link is Up 100 Mbps Full Duplex
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth2
[    2.191922] e100 0000:06:01.0: eth2: addr 0xfcefe000, irq 17, MAC addr 00:e0:b6:03:38:3b
[   17.672574] ADDRCONF(NETDEV_UP): eth2: link is not ready
[ 6437.950268] e100 0000:06:01.0: eth2: NIC Link is Up 100 Mbps Full Duplex
[ 6437.952016] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[ 6448.300006] eth2: no IPv6 routers present
[ 6511.950312] e100 0000:06:01.0: eth2: NIC Link is Down
[ 6513.950267] e100 0000:06:01.0: eth2: NIC Link is Up 100 Mbps Full Duplex
[ 6547.950309] e100 0000:06:01.0: eth2: NIC Link is Down
[ 6565.950266] e100 0000:06:01.0: eth2: NIC Link is Up 100 Mbps Full Duplex
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth3
[    2.218731] e100 0000:06:02.0: eth3: addr 0xfcefd000, irq 18, MAC addr 00:e0:b6:03:38:3a
[   17.692541] ADDRCONF(NETDEV_UP): eth3: link is not ready
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth4
[    2.245437] e100 0000:06:03.0: eth4: addr 0xfcefc000, irq 19, MAC addr 00:e0:b6:03:38:39
[   17.712554] ADDRCONF(NETDEV_UP): eth4: link is not ready
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth5
[    2.272379] e100 0000:07:00.0: eth5: addr 0xfcfff000, irq 255, MAC addr 00:e0:b6:03:38:a8
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth6
[    2.299874] e100 0000:07:01.0: eth6: addr 0xfcffe000, irq 255, MAC addr 00:e0:b6:03:38:a7
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth7
[    2.326678] e100 0000:07:02.0: eth7: addr 0xfcffd000, irq 255, MAC addr 00:e0:b6:03:38:a6
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth8
[    2.353470] e100 0000:07:03.0: eth8: addr 0xfcffc000, irq 255, MAC addr 00:e0:b6:03:38:a5
mrenshaw@gns3-ubuntu:~$ dmesg | grep eth9

```
 
and from an lspci
 
```
mrenshaw@gns3-ubuntu:~$ lspci | grep Ethernet
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
06:01.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
06:02.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
06:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
07:00.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
07:01.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
07:02.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
07:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)

```
 
So my question is why doesn't eth5 - 8 show up with ifconfig?
 
if anyone could offer anyhelp I would be greatful..

---

