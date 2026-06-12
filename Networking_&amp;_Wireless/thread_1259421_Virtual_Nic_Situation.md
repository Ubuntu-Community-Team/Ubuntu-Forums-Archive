---
title: "Virtual Nic Situation"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by vineeth_vijay on 2009-09-06
Hello guys...

I am a university student.Our internet access is via squid proxies,each proxy allowing a maximum of 10 connections per ip.I am thinking of increasing the simultaneous connections to a computer with the help of virtual NIC ie two or three ip's assigned to a single computer and connections going out via each interface thereby making 30 connections to the proxy server.

The problem when i assigned the virtual addresses is that there seems no activity whatsoever in the virtual ip's(TX=0,RX=0)

Here are my questions:
1) How to resolve the problem ie make the virtual ip's active
2) How to add routes such that a connection to say proxy x.x.x.x will divide through all three interfaces ie eth0,eth0:1,eth0:2(I personally think,it can be done via METRIC)

---

### Post by vineeth_vijay on 2009-09-06
Also Here are my network configurations:

FILE:/etc/networks/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 172.31.73.120
        netmask 255.255.255.192
        gateway 172.31.73.65

auto eth0:1
iface eth0:1 inet static
        address 172.31.73.67
        netmask 255.255.255.192
   
auto eth0:2
iface eth0:2 inet static
        address 172.31.73.71
        netmask 255.255.255.192
 
I get this messages on sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * if-up.d/mountnfs[eth0]: waiting for interface eth0:1 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface eth0:2 before doing NFS mounts
SIOCSIFFLAGS: Cannot assign requested address
 * if-up.d/mountnfs[eth0:1]: waiting for interface eth0:2 before doing NFS mounts
SIOCSIFFLAGS: Cannot assign requested address

Here is ifconfig command result
eth0      Link encap:Ethernet  HWaddr 00:16:d3:f5:8b:3c  
          inet addr:172.31.73.120  Bcast:172.31.73.127  Mask:255.255.255.192
          inet6 addr: fe80::216:d3ff:fef5:8b3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2529496 (2.5 MB)  TX bytes:655683 (655.6 KB)
          Interrupt:17 

eth0:1    Link encap:Ethernet  HWaddr 00:16:d3:f5:8b:3c  
          inet addr:172.31.73.67  Bcast:172.31.73.127  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

eth0:2    Link encap:Ethernet  HWaddr 00:16:d3:f5:8b:3c  
          inet addr:172.31.73.71  Bcast:172.31.73.127  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4828 (4.8 KB)  TX bytes:4828 (4.8 KB)

---

