---
title: "DHCP not working"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by b@sh_n3rd on 2009-05-10
Hi...I've just installed Jaunty (To be precise, last night) and am currently in the configuration process. This is my 3rd Jaunty PC BTW, so I was expecting the usual after-installation occurrences. Nevertheless, when I booted my PC this morning and powered up my router I, noticed that my PC wouldn't connect to the network. My network card is an [COLOR=Green]Intel 82557/8/9/0/1 Ethernet Pro 100 (rev 01)[/COLOR]

First, the PC searches for an IP and DNS address via DHCP. It never connects. After a few moments delay, It replies, "[COLOR=Red]Wired Network - Disconnected[/COLOR]" and disables my network card. When I try manual network configuration it hooks up to the network but I have no [COLOR=RoyalBlue]*Internet* [COLOR=Black]connection[/COLOR][/COLOR]. I didn't try local network as yet but assumed that it worked. I haven't really understood how the manual configuration on Ubuntu works so was really not able to hook up to the internet via manual config anyway.

There *were* suspicions that suggested my network card was malfunctioning, but later on it started working correctly. As I recall, I didn't have this prob (or anything similar) the last time I tried Intrepid on this same PC. BTW, this PC was not used for about a month or more. Thanks for all your help. 
#b@sh_n3rd#

---

### Post by superprash2003 on 2009-05-11
post output of **ifconfig** from the terminal.

---

### Post by b@sh_n3rd on 2009-05-11
Here's the output of **ifconfig**:
```
eth0      Link encap:Ethernet  HWaddr 00:a0:c9:03:8d:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:30:4f:39:fd:da  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe39:fdda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1048299 (1.0 MB)  TX bytes:178590 (178.5 KB)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```The card that's giving trouble is eth0, I just *borrowed* a spare Network Adapter from another PC temporarily...One thing is, eth1 works....does this mean I'm having a hardware problem? If so, I'm in trouble...

---

### Post by superprash2003 on 2009-05-11
it seems alright..your eth0 is getting an ip 192.168.1.2 .. by dhcp i presume..

---

### Post by Peter09 on 2009-05-11
post the output of

```
lshw -C network
```
that will give more information about your card

---

### Post by Peter09 on 2009-05-11
Just confirm that eth0 is the problem and eth1 is a spare card

---

### Post by promet on 2009-05-11
Check your "/etc/resolv.conf" file

be sure that this file contains the ip addresses of your DNS Server in the format:

"namesever 192.168.1.1" (I use 192.168.1.1 because it is my own router default, yours may be different)

I've had trouble with Jaunty erasing the content of this file from time to time, why I don't know....

---

### Post by Peter09 on 2009-05-11
Can we see the output of 

```
route
```

---

### Post by Peter09 on 2009-05-11
Just a thought here - we are not going to see the problem when the working card is connected, I think you will have to use the problem card when giving us the output of these commands.

---

### Post by b@sh_n3rd on 2009-05-12
OK, from the top, ifconfig with eth0 plugged in...
```
eth0      Link encap:Ethernet  HWaddr 00:a0:c9:03:8d:40  
          inet6 addr: fe80::2a0:c9ff:fe03:8d40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:11 dropped:0 overruns:0 frame:11
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1494 (1.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:30:4f:39:fd:da  
          inet6 addr: fe80::230:4fff:fe39:fdda/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39715128 (39.7 MB)  TX bytes:1497637 (1.4 MB)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```
Next, lshw -C network;
```
*-network:0             
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 01
       serial: 00:a0:c9:03:8d:40
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth1
       version: 8b
       serial: 00:30:4f:39:fd:da
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:ef:be:82:0e:05
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
Now the last, route;
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

---

### Post by b@sh_n3rd on 2009-05-12
I posted the test on the above post and am replying on this one. The division is so that it's easier to follow...I hope :D. superprash2003, you mean eth1? well...yeah I'm using DHCP... Peter09, eth0 is the problem card and eth1 is the working one. I've plugged eth0 as you instructed. Here's what actually happens, when I plug it, it tries to connect the usual way, but never does...after a moment it says the connection is disconnected and it also gets disabled automatically. promet, I'm gonna check that file now...and yeah, my router address is 192.168.1.1

---

