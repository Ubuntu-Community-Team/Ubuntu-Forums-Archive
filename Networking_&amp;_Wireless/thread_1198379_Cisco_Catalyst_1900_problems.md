---
title: "Cisco Catalyst 1900 problems"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by Kirfew on 2009-06-27
I am going to a small lan party soon, and since I have a Cisco Catalyst 1900 (a switch) I was asked to bring it. I'm testing it out and my windows boxes connect to it fine but my linux box (Ubuntu 8.10) doesn't work. When I plug my ethernet cable in the icon displays the requesting network address animation for about 15 seconds and then disconnects. Any help would be very much appreciated and I really need to get this working since I dont feel like having to use Windows at the LAN.
Here's the output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0c:f1:da:51:1c  
          inet addr:10.0.0.8  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:feda:511c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8367447 (8.3 MB)  TX bytes:1279645 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97801 (97.8 KB)  TX bytes:97801 (97.8 KB)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sit1      Link encap:IPv6-in-IPv4  
          inet6 addr: 2001:470:1f12:e2::2/64 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by DGortze380 on 2009-06-27
Plug into your switch, and try to ping another computer connected to it.

Your switch likely doesn't have a DHCP Server built in, so you'll have to manually assign the addresses. From your ifconfig output, you've already got an address assigned.

---

### Post by Kirfew on 2009-06-27
I tried that, but ping responds with Network unreachable.
How can I use ifconfig to manually give myself an IP address?

---

### Post by DGortze380 on 2009-06-27
> **Kirfew said:**
> I tried that, but ping responds with Network unreachable.
How can I use ifconfig to manually give myself an IP address?

Check the address of all the machines connected to the switch. 
They have to be on the same subnet.

For example, you could use 3 computers connected to the switch with the following.

10.0.0.1 255.255.255.0
10.0.0.2 255.255.255.0
10.0.0.3 255.255.255.0

To assign the address on Ubuntu use 

```

ifconfig [int] [address] netmask [netmask]

```

where [int] is your interface, eth0?
where [address] is your ip address
where [netmask] is your subnet mask

The trick is, the addresses really don't matter with a switch, but the OS is going to want you to assign them.

---

