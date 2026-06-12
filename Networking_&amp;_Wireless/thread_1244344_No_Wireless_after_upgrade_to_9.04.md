---
title: "No Wireless after upgrade to 9.04"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by Dynamize on 2009-08-18
I am sorry if this is the wrong place for this post.

I upgraded to 9.04 last night. I no longer have Wifi support. This is a large issue for me (the network cable is in a really awkward spot.

I have a HP Compaq Presario v2000 with the ram upgraded to 1.5gb (yes it's an old machine but it usually does what I need it to). 

Does anyone know how I can get the Wifi working?

I would be very grateful for any help.

Regards,
David.

---

### Post by philinux on 2009-08-18
> **Dynamize said:**
> I am sorry if this is the wrong place for this post.

I upgraded to 9.04 last night. I no longer have Wifi support. This is a large issue for me (the network cable is in a really awkward spot.

I have a HP Compaq Presario v2000 with the ram upgraded to 1.5gb (yes it's an old machine but it usually does what I need it to). 

Does anyone know how I can get the Wifi working?

I would be very grateful for any help.

Regards,
David.

Yes it is. You should have chosen to start a new thread. your problem is unrelated to the OP. On your own post click the report icon under the been count. Ask the moderators to create a thread from your post.

---

### Post by bapoumba on 2009-08-19
Moved to its own thread. What is the spec of the wireless card ?

---

### Post by superprash2003 on 2009-08-19
do post output of **lshw -C network** from the terminal

---

### Post by Iowan on 2009-08-19
**ifconfig -a** will probably only confirm that wireless interface has no address. Does the wired interface (awkward as it may be) work?

---

### Post by Dynamize on 2009-08-19
> **superprash2003 said:**
> do post output of **lshw -C network** from the terminal


First off let me thank you for getting back to me.

Here is the output from "lshw -C network"

dave@dave-laptop:~$ sudo lshw -C network
sudo: unable to resolve host dave-laptop
[sudo] password for dave:
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:90:04:3d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii
10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too
driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=64 link=yes
maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII
speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:b5:0d:d3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200
driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32
link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes
wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:c5:17:fd:55:f3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3
firmware=N/A link=yes multicast=yes

---

### Post by Dynamize on 2009-08-19
> **Iowan said:**
> **ifconfig -a** will probably only confirm that wireless interface has no address. Does the wired interface (awkward as it may be) work?


Again thanks for the help,

Yes the wired interface does work. 

The output from "ifconfig -a" is

dave@dave-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:90:04:3d  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe90:43d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37193898 (37.1 MB)  TX bytes:1815666 (1.8 MB)
          Interrupt:16 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:b5:0d:d3  
          inet6 addr: fe80::212:f0ff:feb5:dd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2072 errors:1603 dropped:1603 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:15385 (15.3 KB)
          Interrupt:18 Base address:0x8000 Memory:b0107000-b0107fff 

eth1:avahi Link encap:Ethernet  HWaddr 00:12:f0:b5:0d:d3  
          inet addr:169.254.8.101  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8000 Memory:b0107000-b0107fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9256 (9.2 KB)  TX bytes:9256 (9.2 KB)

pan0      Link encap:Ethernet  HWaddr 36:c5:17:fd:55:f3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Dynamize on 2009-08-19
> **bapoumba said:**
> Moved to its own thread. What is the spec of the wireless card ?


Thanks for moving the post to a new Thread for me. Sorry for posting in the wrong place the first time.

I think my wireless card is "PRO/Wireless 2200BG [Calexico2] Network Connection"

---

### Post by bapoumba on 2009-08-20
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366217](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366217)
[http://ubuntuforums.org/showthread.php?t=1134948](http://ubuntuforums.org/showthread.php?t=1134948)

You may find solutions there :)

---

### Post by madhavhmk on 2009-08-20
you can also check out this brilliant step by step tutorial on network issue, 

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)


it worked for me...

---

### Post by Dynamize on 2009-08-20
bapoumba & madhavhmk,

Cheers for the help. I am using a windows machine at work so it's usually about 8 - 9 pm before I get home to work on Ubuntu so I will try your suggestions later. 

Thanks,

David.

---

