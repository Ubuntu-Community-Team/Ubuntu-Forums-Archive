---
title: "Internet not working."
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by virenbt on 2010-12-06
[SIZE=3]Hi all               :popcorn:

I just installed Ubuntu 10.04 on my Lenovo Think Centre PC which is also having windows 7 loaded on it. I am able to use internet (LAN) in Windows but in Ubuntu am not able to use internet. I am beginer to Linux. In Ununtu it's showing no connections. I configured the settings but still its not connecting. It's not detecting any internet connection. Can anybody tell How to fix this problem. 

thanks[/SIZE]     :p

---

### Post by stlsaint on 2010-12-06
Are you trying to use wireless or hard wire?
Also what type of nic card are you running?

---

### Post by dineshs on 2010-12-06
What do you get for```
sudo lshw -C network
```Please post result

---

### Post by virenbt on 2010-12-07
> **stlsaint said:**
> Are you trying to use wireless or hard wire?
Also what type of nic card are you running?


Hi

am using wired network and 
Generic Marvell Yukon 88E8057 PCI-E Gigabit Ethernet Controller

in networks its showing not connected.

thanks

---

### Post by virenbt on 2010-12-07
> **dineshs said:**
> What do you get for```
sudo lshw -C network
```Please post result


viren@Think-Centre:~$ sudo lshw -C network
[sudo] password for viren: 
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 44:37:e6:04:d2:d2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:febfc000-febfffff ioport:e800(size=256) memory:febc0000-febdffff(prefetchable)



viren@Think-Centre:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:37:e6:04:d2:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128686 (128.6 KB)  TX bytes:128686 (128.6 KB)

---

