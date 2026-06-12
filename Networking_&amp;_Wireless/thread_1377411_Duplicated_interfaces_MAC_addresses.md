---
title: "Duplicated interfaces MAC addresses"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by sebaie on 2010-01-10
Hello please help me solve this issue,

I have a machine running ubuntu 8.04 server (custom compiled kernel 2.6.24.6)
4 Ethernet interfaces (8255xER/82551IT Fast Ethernet Controller)

When i boot the system i run #ifconfig -a
i see the following:
```

eth0      Link encap:Ethernet  HWaddr 00:40:63:f1:7a:38
          inet addr:201.202.5.31  Bcast:201.202.5.255  Mask:255.255.255.0
          inet6 addr: fe80::240:63ff:fef1:7a38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6551 errors:6 dropped:0 overruns:0 frame:6
          TX packets:4632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:196 txqueuelen:1000
          RX bytes:881584 (860.9 KB)  TX bytes:1492457 (1.4 MB)

eth1      Link encap:Ethernet  HWaddr 00:40:63:f1:7a:39
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:40:63:f1:7a:3a
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3_rename Link encap:Ethernet  HWaddr 00:40:63:f1:7a:39
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```As you see from the above output there're two interfaces have the same HWaddrs eth1 and eth3_rename

when i run #lshw | grep network
then the output comes like:
```

lshw | grep network
        *-network:0
        *-network:1
        *-network:2
        *-network:3 DISABLED

```i did try to change the name of my interface eth3_rename to eth3 with the correct mac address in the file /etc/udev/rules.d/70-persistent-net.rules then rebooting the machine nothing changed.

how can i change my eth3_rename to eth3 and how to solve the mac address duplicates ? any one had the same problem ?

Thank you all for your help and support.

Mustafa

---

