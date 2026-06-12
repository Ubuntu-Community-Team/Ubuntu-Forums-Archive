---
title: "SIOCADDRT: No such process"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by wraithoffire on 2009-01-25
Hello everyone.  I'm on a college campus network, and it's been not at all pleasant making it agree with Ubuntu, but it's been working reasonably well until just a short bit ago.  Due to some craziness that I don't adequately understand (Fairly noob) I have to shutdown my ethernet, update the dhclient, and turn the ethernet back on each startup before it would recognize the internet, which was working fine.  Now, when I run 
```
sudo dhclient eth1
```
I get
```
...
DHCPACK of 10.147.20.23 from 10.248.20.254
SIOCADDRT: No such process
bound to 10.247.20.25 -- renewal in 709 seconds
```
(There's a fair bit of code before this that hasn't changed)
After I bring eth1 back up, instead of working well and allowing me to surf to my hearts content, I can't connect to the internet.  Any help would be very much appreciated.

---

### Post by nixscripter on 2009-01-26
The message "SIOCADDRT: No such process" means that eth1 is not an interface it can find to give the ethernet the DHCP client got.

When it happens, post the output of **ifconfig -a** and **lshw -C network** from a Terminal to see if the card was, for example, renamed. (Don't forget to use [code] blocks around your post).

---

### Post by wraithoffire on 2009-01-26
ifconfig -a resulted in
```
eth1      Link encap:Ethernet  HWaddr 00:21:97:13:05:e5  
          inet addr:10.247.20.34  Bcast:10.247.23.255  Mask:255.255.252.0
          inet6 addr: fe80::221:97ff:fe13:5e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:661 errors:0 dropped:11678247392 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65334 (63.8 KB)  TX bytes:9069 (8.8 KB)
          Interrupt:253 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88700 (86.6 KB)  TX bytes:88700 (86.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6c:31:2e:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:febe0000-febf0000 
```
and lshw -C network gave me
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:21:97:13:05:e5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.247.20.34 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:31:2e:d1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.52+NETGEAR,02/22/2005,3.1.1.7 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

Edit:  Oh my.  I hadn't noticed the dropped packets before... eleven billion dropped packets can't be a good thing...

---

### Post by nixscripter on 2009-01-28
Alright, it looks there is eth1. I just wanted to make sure.

The other thing I notice is that eth1 seems to have an address. I'm wondering now if the DHCP server is either doing something funny, or is not handling your client well.

The next time it happens, try running this before you shut it down: ```
sudo dhclient -r
``` This will release your DHCP-assigned address explicitly before you ask for a new one.

Also, how are you shutting your ethernet down, exactly? That might also have something to do with it.

---

