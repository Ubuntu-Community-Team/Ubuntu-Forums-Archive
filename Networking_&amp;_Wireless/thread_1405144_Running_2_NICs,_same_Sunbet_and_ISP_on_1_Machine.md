---
title: "Running 2 NICs, same Sunbet and ISP on 1 Machine"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by dannstah on 2010-02-12
Okey, so im running 2 NICs on my Ubuntu Server. Both 2 NICs reicives IP-addresses from the ISP, but the problem is that I can't access Internet, but if I shutdown one of the NICs I works great to access Internet. 

The reason why I wan't to run 2 NICs is:

1. Change Apache2 Listening IP to listen on ETH0
2. SSH and Ventrilo Listening on ETH1

My /etc/network/interface

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


```ifconfig

```


eth0      Link encap:Ethernet  HWaddr 00:19:b9:1e:04:b7
          inet addr:81.170.xxx.xxx  Bcast:81.170.xxx.xxx  Mask:255.255.xxx.xxx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11443193 (11.4 MB)  TX bytes:791245 (791.2 KB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:23:cd:b0:da:1e
          inet addr:81.170.xxx.xxx  Bcast:81.170.xxx.xxx  Mask:255.255.xxx.xxx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:264530 (264.5 KB)  TX bytes:2164 (2.1 KB)
          Interrupt:18 Base address:0xcf00


```I think it have something to do with IP Route

---

### Post by Iowan on 2010-02-12
What are results of **route -n**? Two interfaces in the same subnet tends to play havoc with routing - I'm a bit surprised you could get IP addresses for both.

---

### Post by dannstah on 2010-02-12
> **Iowan said:**
> What are results of **route -n**? Two interfaces in the same subnet tends to play havoc with routing - I'm a bit surprised you could get IP addresses for both.

The ISP gives out 10 public ip-addresses per household

**route -n**
```

81.170.140.0    0.0.0.0         255.255.254.0   U     0      0        0 eth0
81.170.140.0    0.0.0.0         255.255.254.0   U     0      0        0 eth1
0.0.0.0         81.170.140.1    0.0.0.0         UG    100    0        0 eth1
0.0.0.0         81.170.140.1    0.0.0.0         UG    100    0        0 eth0

```

---

### Post by Iowan on 2010-02-12
Two default gateways creates even more problems. You may be able to create some **iptables** rules to send packets the right direction.  You can see if [this]("http://ubuntuforums.org/showpost.php?p=8142708&postcount=8") helps - at least short term (dunno if it'll survive a reboot).

---

### Post by dannstah on 2010-02-12
> **Iowan said:**
> Two default gateways creates even more problems. You may be able to create some **iptables** rules to send packets the right direction.  You can see if [this]("http://ubuntuforums.org/showpost.php?p=8142708&postcount=8") helps - at least short term (dunno if it'll survive a reboot).

Sorry to bother you but I dont fully understand what to do....

---

### Post by mips on 2010-02-12
Having two ethernet adapters in the same subnet is not on.

---

### Post by dannstah on 2010-02-12
> **mips said:**
> Having two ethernet adapters in the same subnet is not on.

Do you mean it isnt possible? Or do i have to "activate" something?

---

### Post by mips on 2010-02-12
See post#11 [http://ubuntuforums.org/showthread.php?t=117356](http://ubuntuforums.org/showthread.php?t=117356)
or 
[http://www.ncsa.illinois.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/aixbman/commadmn/tcp_interfaces.htm](http://www.ncsa.illinois.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/aixbman/commadmn/tcp_interfaces.htm)

> **Implications of Multiple Network Interfaces on the Same Network**

Sometimes network managers feel the need to provide greater availability and performance by adding a second network adapter to a particular machine. For example, they may want to have two token-ring adapters attached to the same physical network. While it is possible to have more than one interface on the same network, in general this is not recommended for two reasons:

1. Having two interfaces on the same network is a **[COLOR="Red"]violation of TCP/IP architecture[/COLOR]**.

In TCP/IP architecture, a host machine with two network adapters is defined as an IP router. Different network adapters must be attached to different physical networks. In the case of token-ring, TCP/IP addresses multiple rings bridged together as a single logical ring (as if it were a single physical ring).

2. Having two interfaces on the same network can cause broadcast storms.

Whenever an IP host sees traffic for a network whose IP address is different from its own network, it generates an Internet Control Message Protocol (ICMP) packet announcing this conflict. Since every host on the network sees the traffic that is misaddressed, every host generates ICMP packets. If the amount of misaddressed traffic is significant, the ICMP traffic can grow to the point that network performance degrades.

It is possible to avoid the broadcast storms created when multiple interfaces are connected to the same network. However, doing so is still a violation of TCP/IP architecture. The solution is to give the different interfaces different IP addresses on the same network. For example, you might have two token-ring adapters on the same network named tr0 and tr1. You must assign distinct IP addresses and names to tr0 and tr1. (TCP/IP architecture requires that each interface have a unique IP address and name; otherwise, unpredictable behavior will result.) For instance, you might give interface tr0 the IP address 10.10.10.1 and the name laurel.foo.bar.com, and interface tr1 the IP address 10.10.10.2 and the name hardy.foo.bar.com.

---

### Post by madzieph on 2010-02-12
It seems that your purpose of having 2 NICs is to "create" separate paths for certain data... as stated above having 2 NICs do create some problems. One solution maybe to bond those NICs into one virtual interface.

Search for bonding or link aggregation.

Hope this helps.

---

