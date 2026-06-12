---
title: "Ubuntu box can ping LAN but not WAN"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by kapu222 on 2009-05-24
:-(

Linux coldenftp 2.6.24-19-server #1 SMP Wed Jun 18 15:18:00 UTC 2008 i686

**[COLOR=Red]ifconfig /all[/COLOR]**
/all: error fetching interface information: Device not found


[COLOR=Red]**ifconfig -a**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:a0:c9:e4:5c:20  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fee4:5c20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7694100 (7.3 MB)  TX bytes:808280 (789.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**[COLOR=Red]cat /etc/resolv.conf[/COLOR]**
search workgroup
nameserver 192.168.2.1

**[COLOR=Red]ping -c3 74.125.65.147[/COLOR]**
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.

--- 74.125.65.147 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2006ms

[COLOR=Red]**ping -c3 192.168.2.1**[/COLOR]
ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=8.38 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.775 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.783 ms

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 0.775/3.313/8.383/3.585 ms

**[COLOR=Red]lshw -C network[/COLOR]**
PCI (sysfs)  

  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 02
       serial: 00:a0:c9:e4:5c:20
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.2.2 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by rudy.b on 2009-05-24
Do you have other systems on the LAN that are able to ping WAN?  i.e. can you verify that your router is connected to the Internet?  If not, you can try resetting the router to see if that will establish a connection.

---

### Post by kapu222 on 2009-05-24
> **rudy.b said:**
> Do you have other systems on the LAN that are able to ping WAN? i.e. can you verify that your router is connected to the Internet? If not, you can try resetting the router to see if that will establish a connection.
 
Yes, I have several hosts that are on this LAN that use the same router, and there is no problem with connectivity. I access the crippled box in question via ssh with no problems from a laptop on the LAN.

---

### Post by Iowan on 2009-05-24
Post results of **route -n**... I'm wondering if it has gateway problem.

---

### Post by kapu222 on 2009-05-24
> **Iowan said:**
> Post results of **route -n**... I'm wondering if it has gateway problem.
 
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by kapu222 on 2009-05-24
I rebooted the machine and now I can ping. :oops:
 
Thank you Rudy.b and Iowan
 
Case closed.

---

