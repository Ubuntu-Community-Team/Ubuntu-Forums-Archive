---
title: "I can't access the internet, despite the machine connecting to my wireless network"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by Cancambo on 2010-10-06
Alright, so I decided I wanted to try Ubuntu the other day.  So far, everything has been fine, except getting my wireless internet to work.  I have a USR2216 wireless adapter, and no possibility for a wired connection.  At first, I tried to figure out ACX100, but I got hopelessly lost.  I then moved on to NDISwrapper, which I did get to work.  My machine now recognizes the device, and recognizes wireless networks.  However, the computer will not access websites.  I had a thought that it could possibly be a DNS server issue, so I setup OpenDNS, and it still didn't work.  I am currently on my Windows partition and everything works fine here.  I really have no idea what to do, I am completely lost.  I will run any commands I need to later and then post them here. (Luckily I have a second HDD so I can transfer fiels from OS to OS).

This is the result of the ifconfig I ran yesterday before I loaded up the drivers for NDISwrapper today.  Leaving it here jsut in case it helps.
```

matt@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:55:82:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

  *-network:0 UNCLAIMED   
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: ioport:dc00(size=32) memory:ff8ff000-ff8fffff memory:ff8e0000-ff8effff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 82
       serial: 00:11:11:55:82:58
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:ff8fe000-ff8fefff ioport:d800(size=64)
```

EDIT: I ran a ton of commands from that sticked thread. [http://pastebin.com/wJzD1mpN](http://pastebin.com/wJzD1mpN)

I have an eMachines T2893 PC, a USR2216 wireless card, and Ubuntu 10.04.

---

### Post by abhi2706 on 2010-10-07
Normally, "ifconfig" command gives the IP address list assigned to your machine on specific interface.
But the output that you have provided, has only following::
inet addr: 127.0.0.1


Can you check after connecting to Wireless Network, some LAN IP is provided to your machine ????

---

### Post by Cancambo on 2010-10-07
> **abhi2706 said:**
> Normally, "ifconfig" command gives the IP address list assigned to your machine on specific interface.
But the output that you have provided, has only following::
inet addr: 127.0.0.1


Can you check after connecting to Wireless Network, some LAN IP is provided to your machine ????

I ran this one and I still got 127.0.0.1, and this was with it saying I was connected to my network.

```
matt@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:55:82:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137236 (137.2 KB)  TX bytes:137236 (137.2 KB)
```

Should I just try to ditch NDISwrapper and go for acx?

---

### Post by dineshs on 2010-10-07
eth0 is your wired interface.(82801DB PRO/100 VE (LOM) Ethernet Controller)
From the result of lshw> *-network:0 UNCLAIMED   
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
the wireless interface is ACX 100 
Please see if the guidelines given by chili555 in [this]("http://ubuntuforums.org/showthread.php?t=860203&page=2") thread helps

---

