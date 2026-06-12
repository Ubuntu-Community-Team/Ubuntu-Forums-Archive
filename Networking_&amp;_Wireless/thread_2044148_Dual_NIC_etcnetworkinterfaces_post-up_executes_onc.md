---
title: "Dual NIC /etc/network/interfaces post-up executes once"
date: 2012-08-18
forum: Networking &amp; Wireless
---

### Post by jswan on 2012-08-18
Hello, I'm having issues getting a post-up script to work as I would expect I would expect it to.  The scripts and interfaces configuration as shown below.  My *final* intention is to configure eth0 as the primary/pure interface and vpn traffic forwarded through eth1.  Both eth0 and eth1 connect to the same gateway router.  I plan on configuring squid3 to filter certain domains (youtube.com) through the vpn to avoid my throttling from my isp.

System information:
Ubuntu Server
Linux maple 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


Here is a brief layout of my goal:
```

client1--\              /-- nic0 --\ - - - - - - -/--------------\
          \            /            \            /                \
           >--server-->              >--router-->                  >--INTERNET!!
          /            \            /            \                /
clientX--/              \-- nic1 --/ - - - - - - -\--vpn tunnel--/

```

Any help or advice is much appreciated!


Contents of /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# Define the network's nameserver

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
   address     192.168.1.11
   netmask     255.255.255.0
   network     192.168.1.0
   broadcast   192.168.1.255
   gateway     192.168.1.1
   dns-nameservers 192.168.1.1
   post-up /etc/network/scripts/iproute2

# The secondary network interface
auto eth1
iface eth1 inet static
   address     192.168.1.12
   netmask     255.255.255.0
   network     192.168.1.0
   broadcast   192.168.1.255
   gateway     192.168.1.1
   dns-nameservers 192.168.1.1
   post-up /etc/network/scripts/iproute2

```

Contents of /etc/network/scripts/iproute2
```

#!/bin/bash

echo stag0 $IFACE >> /root/ifconfig-status
awk '{print $1*1000}' /proc/uptime $IFACE >> /root/ifconfig-status
ip route add $IF_NETWORK dev $IFACE src $IF_ADDRESS table $IFACE
echo stag1 $IFACE >> /root/ifconfig-status
awk '{print $1*1000}' /proc/uptime $IFACE >> /root/ifconfig-status
ip route add default via $IF_GATEWAY dev $IFACE table $IFACE
echo stag2 $IFACE >> /root/ifconfig-status
awk '{print $1*1000}' /proc/uptime $IFACE >> /root/ifconfig-status
ip route add $IF_GATEWAY dev $IFACE src $IF_ADDRESS
echo stag3 $IFACE >> /root/ifconfig-status
awk '{print $1*1000}' /proc/uptime $IFACE >> /root/ifconfig-status
ip rule add from $IF_ADDRESS table $IFACE
echo stag4 $IFACE >> /root/ifconfig-status
awk '{print $1*1000}' /proc/uptime $IFACE >> /root/ifconfig-status
ip rule add iif $IFACE table $IFACE
echo stag5 $IFACE >> /root/ifconfig-status
awk '{print $1*1000}' /proc/uptime $IFACE >> /root/ifconfig-status
ip rule add oif $IFACE table $IFACE
echo stag6 $IFACE >> /root/ifconfig-status
awk '{print $1*1000}' /proc/uptime $IFACE >> /root/ifconfig-status
exit 0

```

Output of /root/ifconfig-status
```

stag0 eth1
17690
stag1 eth1
17710
stag2 eth1
17720
stag3 eth1
17720
stag4 eth1
17730
stag5 eth1
17740
stag6 eth1
17750

```

Output of dmesg | grep eth
```
    
[    0.124704] i2c-core: driver [aat2870] using legacy suspend method
[    0.124706] i2c-core: driver [aat2870] using legacy resume method
[    1.634615] r8169 0000:04:00.0: eth0: RTL8168c/8111c at 0xffffc90000324000, 00:24:1d:2f:32:fe, XID 1c4000c0 IRQ 45
[    1.634620] r8169 0000:04:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.669335] r8169 0000:05:00.0: eth1: RTL8168c/8111c at 0xffffc90000326000, 00:1f:d0:81:6f:bc, XID 1c4000c0 IRQ 46
[    1.669340] r8169 0000:05:00.0: eth1: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[   16.750195] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.750204] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.609736] r8169 0000:05:00.0: eth1: link down
[   17.609745] r8169 0000:05:00.0: eth1: link down
[   17.614346] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.620468] r8169 0000:04:00.0: eth0: link down
[   17.620477] r8169 0000:04:00.0: eth0: link down
[   17.627320] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.640993] r8169 0000:05:00.0: eth1: link up
[   20.641252] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   20.643020] r8169 0000:04:00.0: eth0: link up
[   20.643269] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```


Output form ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe2f:32fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:116469 (116.4 KB)  TX bytes:32443 (32.4 KB)
          Interrupt:45 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe81:6fbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:646852 (646.8 KB)  TX bytes:442311 (442.3 KB)
          Interrupt:46 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1880 (1.8 KB)  TX bytes:1880 (1.8 KB)

```

Output from ip rule show
```

0:      from all lookup local
32763:  from all oif eth1 lookup eth1
32764:  from all iif eth1 lookup eth1
32765:  from 192.168.1.12 lookup eth1
32766:  from all lookup main
32767:  from all lookup default

```

Output from ip route show
```

default via 192.168.1.1 dev eth1  metric 100
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.12
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.11
192.168.1.1 dev eth1  scope link  src 192.168.1.12

```

Output from ip route show table eth0
```


```

Output from ip route show table eth1
```

default via 192.168.1.1 dev eth1
192.168.1.0 dev eth1  scope link  src 192.168.1.12

```

---

### Post by jswan on 2012-08-19
Issue resolved.

The problem was defining the same gateway for both interfaces.  Which ever interface came up first would successfully complete the internal configuration, then run the script, however, the second interface to come up would fail the internal configuration and not call the script.

The script relied on $IF_GATEWAY variable being set, so I have to abandon my script approach.  Another thing that me be of interest is the following line in man interfaces(5):

```
The  following  "command"  options are available for every family and method.  Each of these options can be given multiple times in a single stanza, in which case the commands are executed in the order in which they appear in the stanza.  (You can ensure a command never fails by suffixing "|| true".)
```

From my experience it seemed that if any command did fail, the interface would be stuck in an uncorrectable state requiring a system restart.


Final Configuration (/etc/network/interfaces):

```
 1 # This file describes the network interfaces available on your system
 2 # and how to activate them. For more information, see interfaces(5).
 3
 4 # The loopback network interface
 5 auto lo
 6 iface lo inet loopback
 7
 8 # The primary network interface
 9 auto eth0
10 iface eth0 inet static
11    address     192.168.1.11
12    netmask     255.255.255.0
13    gateway     192.168.1.1
14    # Setup routing.
15    post-up ip route add 192.168.1.0/24 dev eth0 src 192.168.1.11 table eth0 || /bin/true
16    post-up ip route add default via 192.168.1.1 dev eth0 table eth0 || /bin/true
17    post-up ip rule add oif eth0 table eth0 || /bin/true
18    # Teardown routing.
19    post-down ip rule del oif eth0 table eth0 || /bin/true
20
21 # The secondary network interface
22 auto eth1
23 iface eth1 inet static
24    address     192.168.1.12
25    netmask     255.255.255.0
26    # Setup routing.
27    post-up ip route add 192.168.1.0/24 dev eth1 src 192.168.1.12 table eth1 || /bin/true
28    post-up ip route add default via 192.168.1.1 dev eth1 table eth1 || /bin/true
29    post-up ip rule add oif eth1 table eth1 || /bin/true
30    # Teardown routing.
31    post-down ip rule del oif eth1 table eth1 || /bin/true
32
```

---

