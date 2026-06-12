---
title: "Dell 1420 wireless down after update"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by DaviswhoisDavis on 2008-12-06
Hello,

I am both new to Ubuntu and travelling in Southeast Asia.  Last week I updated the recommended updates and when I rebooted, My wireless was down. The network connection icon does not even recognise the existance of eth1 and when I go to manual configuration there is no option for a wireless connection.  

Here is what I've been able to tease from the terminal with my slight understanding.

davis@dell:~$ sudo lshw -C network
[sudo] password for davis:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:ff:6b:04
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.1.106 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
davis@dell:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:ff:6b:04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 ip=192.168.1.106 latency=0 module=tg3 multicast=yes
davis@dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

davis@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:A0:FF:6B:04  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:feff:6b04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6236752 (5.9 MB)  TX bytes:576556 (563.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Any and all help is appreciated.  Thanks

---

