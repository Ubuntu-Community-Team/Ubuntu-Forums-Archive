---
title: "Intermittent internet connection"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by DWMoreau on 2012-11-05
Hello,

I am using Ubuntu 12.04 and have issues with my internet through the school's wifi connection. It might work for a while, then will cut-off and might not start working again. One interesting thing I have noticed is that my Dropbox folder will sync randomly when I cannot connect to the internet.

I can connect to the network, but the internet will not work. I can ping localhost.

I have no problems with the internet in other places.

Here are a some results of investigations that I have done:

ifconfig
```
david@William:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d2:bb:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14514 (14.5 KB)  TX bytes:14514 (14.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:8d:8d:94  
          inet addr:152.14.234.143  Bcast:152.14.235.255  Mask:255.255.254.0
          inet6 addr: fe80::21f:e1ff:fe8d:8d94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573637 (573.6 KB)  TX bytes:40365 (40.3 KB)
```ping localhost
```
david@William:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.057 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.055 ms
64 bytes from localhost (127.0.0.1): icmp_req=3 ttl=64 time=0.058 ms
64 bytes from localhost (127.0.0.1): icmp_req=4 ttl=64 time=0.060 ms
64 bytes from localhost (127.0.0.1): icmp_req=5 ttl=64 time=0.057 ms
64 bytes from localhost (127.0.0.1): icmp_req=6 ttl=64 time=0.057 ms
^C
--- localhost ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 0.055/0.057/0.060/0.006 ms
```

---

### Post by DWMoreau on 2012-11-07
I tried decreasing the MTU and that did not work. Any other advice?

---

### Post by uncaspi on 2012-11-07
Please post the contest of sudo lshw -C network

---

### Post by DWMoreau on 2012-11-09
Here you go, Thanks for the help.

```
david@William:~$ sudo lshw -c network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:d2:bb:eb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:8d:8d:94
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-32-generic-pae firmware=N/A ip=152.14.235.219 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:df2f0000-df2fffff
```

---

