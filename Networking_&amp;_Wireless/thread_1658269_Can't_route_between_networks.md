---
title: "Can't route between networks"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by chielchiel on 2011-01-02
Hi all,

I have been trying to setup routing between two private networks with a ubuntu 10.10 server that has two ethernet interfaces. I tried various options and spend much time on it trying to make it work that I decided to reinstall Ubuntu just a few minutes ago.

I have the following network with three machines.

```

###################
# host 1          #
# ip: 172.16.0.50 #
# gw: 172.16.0.1  #
###################
       |
       |
       |
########################
# ubuntu 10.10 server  #
# ip eth0: 172.16.0.50 #
# ip eth1: 172.16.0.1  #
########################
       |
       |
       |
###################
# host 2          #
# ip: 10.0.0.1    #
# gw: n/a         #
###################


```

I have configured the interfaces on the ubuntu router with that information:

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:78:99:fa  
          inet addr:172.16.0.1  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe78:99fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:797 (797.0 B)  TX bytes:468 (468.0 B)
          Interrupt:16 Base address:0x1000 

eth1      Link encap:Ethernet  HWaddr 00:40:ca:84:7a:3e  
          inet addr:10.0.0.13  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::240:caff:fe84:7a3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82194 (82.1 KB)  TX bytes:95156 (95.1 KB)
          Interrupt:20 

```

I enabled routing by by uncommeting "net.ipv4.ip_forward=1" in /etc/sysctl.conf, after a restart I can see that routing is enabled:

```

$ cat /proc/sys/net/ipv4/ip_forward
1

```

I have the following routing table on the ubuntu router

```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.0.0      *               255.255.255.0   U     0      0        0 eth0
10.0.0.0        *               255.0.0.0       U     0      0        0 eth1
default         10.0.0.1        0.0.0.0         UG    100    0        0 eth1

```

So all looks good in my believe. However I can't ping between the two hosts. I can however ping from the ubuntu router the two hosts. So something is wrong with the routing, however I don't know where to look for as with the simple above configuration routing should work as I understand. Remember this is a clean install where I only configured the above.

Btw, I didn't change anything in iptables so the problem is not there either.
```

$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      

```

I even replaced the ubuntu router with a simple cisco router with a very basic configuration, with a simple cisco router in place all works oke. So the problem is not with the two host either.

Did I missed something that I need to configure in ubuntu to setup routing?

Kind regards,
chiel

---

### Post by chielchiel on 2011-01-02
As an addition, on host 1 there is a default gateway that point to the ubuntu router. On host 2 there is a static route to point to the 172.16.0.0/24 network.

---

