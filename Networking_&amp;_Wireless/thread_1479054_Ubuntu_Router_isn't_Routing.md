---
title: "Ubuntu Router isn't Routing"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by donaldvr on 2010-05-10
**Summary**
I've set up an ubuntu machine to act as a router with DHCP.  It seems to be working except that computers on the LAN side of the router cannot communicate with the WAN side.  Only the router itself is able to communicate with both sides.
**Background**
Our office is currently using a cheap d-link router.  Although it has a wide range of functionality, I'd like to eventually replace it with an Ubuntu box so that I have more control and the possibility of implementing more advanced features than our d-link offers.  To experiment with using an ubuntu box as a router, I've come up with the following setup, using my work desktop as the router:
[IMG]http://www.quinity-online.com/ubuntuforums/dhcp_layout.png[/IMG]
A - My Desktop (acting as a router and DHCP server)
B - Test Desktop DHCP client. (This computer should be able to connect to C AND anything on the internet.
C - Another computer on the office network.
**The Problem**
When I connect B to the second nic (eth1) on A it is assigned an ip address (192.168.2.100).  B can ping A (192.168.2.1 and 192.168.1.200), but B cannot ping C (192.168.1.20) or google.com, even though A can.ping both of those.

**Additional Information**
On computer A:
```
$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:29:a4:8e:97  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fea4:8e97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69002604 (69.0 MB)  TX bytes:62851736 (62.8 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:80:c8:3a:54:05  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:fe3a:5405/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121890 (121.8 KB)  TX bytes:66790 (66.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61428458 (61.4 MB)  TX bytes:61428458 (61.4 MB)
```

On computer B:
```

$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:0c:b8:d7  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe0c:b8d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360716 (360.7 KB)  TX bytes:135139 (135.1 KB)
          Interrupt:25 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1632 (1.6 KB)  TX bytes:1632 (1.6 KB)

```

Any help is greatly appreciated!

---

### Post by Iowan on 2010-05-10
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for ICS - hopefully it'll help.

---

### Post by iponeverything on 2010-05-11
try turning ipforwarding.

```
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
```

Make sure that computer C has route pointing back to computer A for 192.168.2.0/24 so that the ping responses can reach Network B.

Or you could put the 192.168.2.0/24 route on the D-Link pointing back to computer A.

---

### Post by donaldvr on 2010-05-11
Hey guys, I implemented the ICS guide (including your suggestion to enable forwarding, ipone) and it worked perfectly.

It's especially great to get help from a fellow Iowan.

**One other thing**

On the bottom of the [ubuntu router guide]("https://help.ubuntu.com/community/Router") (which is what I started with) there are links to guides on firewall, dhcp, and dns.  Wouldn't it make sense to have a link to [internet connection sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing") as well?  How can I make that happen so that others won't run into the same problem as I did?

---

