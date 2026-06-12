---
title: "nic bonding latency problem"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by idyllik on 2011-09-05
I'm currently trying to bond two intel nic's(pci cards) which appears to be successful
```
Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 500
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:07:e9:10:6f:06

Slave Interface: eth2
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:07:e9:10:71:80
```

now the problem is after about 10-30 minutes of use the latency will go from 1-7ms and jump between 200-3000ms
reboot doesn't seem to fix anything for long, after about the same period of time bam latency jumps up again

odd thing is, if I plug in the onboard nic into the network everything suddenly works as it should whether it be plugged in on boot or plugged in as soon as the latency jumps up

my config files are as follows
/etc/modules:
```
bonding mode=balance-rr miimon=500
```

/etc/network/interfaces:
```
# ifenslave
    auto bond0
    iface bond0 inet manual
        up ifconfig bond0 up
        up ifenslave bond0 eth1 eth2
        up dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.bond0.pid -lf /var/lib/dhcp3/dhclient.b$
        down ifenslave -d bond0 eth1 eth2
```

ifconfig:
```
ifconfig
bond0     Link encap:Ethernet  HWaddr 00:07:e9:10:6f:06  
          inet addr:192.168.0.120  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe10:6f06/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:18021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1558262 (1.5 MB)  TX bytes:34411428 (34.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:22:15:f1:13:47  
          inet addr:192.168.0.125  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fef1:1347/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1074 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1581040 (1.5 MB)  TX bytes:632927 (632.9 KB)
          Interrupt:30 

eth1      Link encap:Ethernet  HWaddr 00:07:e9:10:6f:06  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:8778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:755189 (755.1 KB)  TX bytes:17200456 (17.2 MB)

eth2      Link encap:Ethernet  HWaddr 00:07:e9:10:6f:06  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:9243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:803073 (803.0 KB)  TX bytes:17210972 (17.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60636 (60.6 KB)  TX bytes:60636 (60.6 KB)
```

am I doing something wrong here? any reason why it'd function fine with the onboard nic plugged in too but freak out when it's not there?

---

