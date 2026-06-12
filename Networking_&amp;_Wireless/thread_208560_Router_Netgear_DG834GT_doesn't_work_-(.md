---
title: "Router Netgear DG834GT doesn't work :-("
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by leone8 on 2006-07-03
Hi,
my internet connection in Ubuntu live cd works perfectly,
but in installed version it doesn't works :( 

 These are all data you may need:

- Router ADSL Netgear DG834GT

 **[CENTER]Connection via ethernet[/CENTER]**
   eth0 is active.
   Enable this connection:    yes.

   Configuration:	  Static IP address
   IP address:	          192.168.0.2
   Subnet mask: 	255.255.255.0
   Gateway address:   192.168.0.1

- Server DNS
  192.168.0.1  ( on live cd it works ok!)

*************************************
**[CENTER]ifconfig statement[/CENTER]**

eth0      Link encap:Ethernet  HWaddr 00:60:6E:75:AD:A0
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::260:6eff:fe75:ada0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:67968 (66.3 KiB)
          Interrupt:11 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:76647 (74.8 KiB)  TX bytes:76647 (74.8 KiB)

**************************************
[B][CENTER]
interfaces file[/CENTER][/B]

/etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

***************************************

**[CENTER]Ping statement[/CENTER]**

ping -c 5 192.168.0.2

PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=0.046 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=0.060 ms
64 bytes from 192.168.0.2: icmp_seq=4 ttl=64 time=0.059 ms
64 bytes from 192.168.0.2: icmp_seq=5 ttl=64 time=0.025 ms

--- 192.168.0.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.025/0.050/0.063/0.016 ms

=========================================================

ping -c 5 192.168.0.1

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable
From 192.168.0.2 icmp_seq=4 Destination Host Unreachable
From 192.168.0.2 icmp_seq=5 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 3999ms
, pipe 3

---

### Post by leone8 on 2006-07-04
up, please !:D

---

### Post by cyberdyne on 2006-07-04
[QUOTE=leone8]up, please !:D[/QUOTE]

Sorry not to have a solution for you, but dont despair as I can assure you the DG834GT works perfectly well with Ubuntu.

I have a WinXP PC on Lan to my DG834GT, with Ubuntu on a second drive in the same machine with internet working perfectly. I also have a WinXP laptop connected via wireless to the router, also without internet problems. 

Im almost setup with my network too, with my Ubuntu seeing and reading my networked files well, im just having a few problems getting windows to see my Ubuntu shares.

However, like I say, keep going, as the router is not your problem.

---

### Post by tturrisi on 2006-07-04
The router is working.
You can ping yourself no problems sending or receiving.  You can ping the gatewaye and send but cannot receive.  This is usually caused by one of the following:
1. firewall blocks received packets.
2. bad cat5 cable
3. some other reason best known to God & sweatshop employees.

---

### Post by leone8 on 2006-07-05
It's all solved:
my ethernet card didn't work fine... I replaced it with another and now it's good!
:D 

Bye !

---

