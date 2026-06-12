---
title: "Ubuntu 12.04 KVM : Guest Machine Can't connect to the Network!"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by THPubs on 2012-09-14
Just stup KVM on my Ubuntu 12.04 exactly according to your guide. But, the guest machine can't connect to the network. It can't get an ip through DHCP and it won't work even if I manually set the IP. Please help!

The  /etc/network/interfaces file in the host :

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

ifconfig results of the bridge :

```
br0       Link encap:Ethernet  HWaddr d0:27:88:b0:e4:38  
          inet addr:192.168.20.100  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::d227:88ff:feb0:e438/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8252 (8.2 KB)  TX bytes:7924 (7.9 KB)

eth0      Link encap:Ethernet  HWaddr d0:27:88:b0:e4:38  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9148 (9.1 KB)  TX bytes:7970 (7.9 KB)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 76:58:19:00:d8:81  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by THPubs on 2012-09-15
I just discovered the problem! Its the firewall! If I disable the firewall, everything works fine! Anyone know how to make it work with the firewall enabled?

---

