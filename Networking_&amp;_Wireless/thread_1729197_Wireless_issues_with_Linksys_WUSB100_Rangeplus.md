---
title: "Wireless issues with Linksys WUSB100 Rangeplus"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by timtincher on 2011-04-14
Ubuntu can only hold a brief amount of time connected to the Internet while using this adapter. I've been trying to download things from the terminal and every time while doing so, the Internet is disconnected so I unplug the adapter then plug it back in and it will work for a little while. How can I fix this problem.

I am running a dual boot with Windows XP. Ubuntu Maverick Meerkat. Linksys WUSB100 Rangeplus

---

### Post by timtincher on 2011-04-14
Some info. Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1737:0070 Linksys WUSB100 RangePlus Wireless USB Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tim@Studio:~$ lshw -C network
WARNING: you should run this program as super-user.
^[[C^[[C^[[C^[[C^[[Csudo su
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       serial: 00:11:11:4d:5f:fa
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 mingnt=255 multicast=yes
       resources: irq:18 memory:fe8e0000-fe8fffff ioport:cf40(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 00:1e:e5:e6:68:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-22-generic firmware=N/A ip=192.168.0.140 multicast=yes wireless=IEEE 802.11bgn
tim@Studio:~$ sudo su
s[sudo] password for tim: 
root@Studio:/home/tim# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1737:0070 Linksys WUSB100 RangePlus Wireless USB Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Studio:/home/tim# ^C
root@Studio:/home/tim# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       serial: 00:11:11:4d:5f:fa
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:fe8e0000-fe8fffff ioport:cf40(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 00:1e:e5:e6:68:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-22-generic firmware=N/A ip=192.168.0.140 link=yes multicast=yes wireless=IEEE 802.11bgn
root@Studio:/home/tim# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:4d:5f:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13088 (13.0 KB)  TX bytes:13088 (13.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:e6:68:8f  
          inet addr:192.168.0.140  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fee6:688f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19827 (19.8 KB)  TX bytes:11411 (11.4 KB)

root@Studio:/home/tim# ^C
root@Studio:/home/tim# rfkill unblock all
root@Studio:/home/tim# dmesg | tail
[  628.936020] wlan0: direct probe to 00:24:01:6f:36:f7 (try 3)
[  629.136020] wlan0: direct probe to 00:24:01:6f:36:f7 timed out
[  639.854300] wlan0: direct probe to 00:24:01:6f:36:f7 (try 1)
[  640.052024] wlan0: direct probe to 00:24:01:6f:36:f7 (try 2)
[  640.252024] wlan0: direct probe to 00:24:01:6f:36:f7 (try 3)
[  640.452020] wlan0: direct probe to 00:24:01:6f:36:f7 timed out
[  651.169827] wlan0: direct probe to 00:24:01:6f:36:f7 (try 1)
[  651.368021] wlan0: direct probe to 00:24:01:6f:36:f7 (try 2)
[  651.568030] wlan0: direct probe to 00:24:01:6f:36:f7 (try 3)
[  651.768019] wlan0: direct probe to 00:24:01:6f:36:f7 timed out

---

