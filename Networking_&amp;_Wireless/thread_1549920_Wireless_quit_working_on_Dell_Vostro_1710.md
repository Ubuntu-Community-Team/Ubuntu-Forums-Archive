---
title: "Wireless quit working on Dell Vostro 1710"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by wavevector on 2010-08-10
Hello all,

I am new to this forum and new to Ubuntu.  I recently installed Ubuntu 10.4 on my Dell Vostro 1710 laptop.  I have partitioned the drives to run both Ubuntu and the operating system that came with the computer, Windows Vista.

Anyhow, I cannot get the wireless to work.  It still works under Vista so I do not think I have a hardware problem.

I have review a few previous threads that seemed to deal with the same problem I am having and have tried some of their fixes (modifying the blacklist.conf file with 'blacklist dell-laptop' - that did not work; modifying the nm-systems-setting.conf file 'managed = true' - that did not work).  Here are some commands I tried and the systems responses:

---------------------------------------------------------------------------------------
john@jsc:~$ sudo lshw -C network
[sudo] 
password for john: 
  
*-network                    
description: Network controller     
product: BCM4312 802.11b/g      
vendor: Broadcom Corporation     
physical id: 0     
bus info: pci@0000:06:00.0    
version: 01       
width: 64 bits       
clock: 33MHz       
capabilities: pm msi pciexpress bus_master cap_list      
configuration: driver=b43-pci-bridge latency=0      
resources: irq:19 memory:f4000000-f4003fff

*-network       
description: Ethernet interface       
product: RTL8111/8168B PCI Express Gigabit Ethernet controller      
vendor: Realtek Semiconductor Co., Ltd.       
physical id: 0     
bus info: pci@0000:07:00.0       
logical name: eth0      
version: 02    
serial: 00:21:70:f1:40:57      
size: 10MB/s      
capacity: 1GB/       
width: 64 bits      
clock: 33MHz      
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation      
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s     
resources: irq:28 ioport:5000(size=256) memory:f8610000-f8610fff(prefetchable) memory:f8600000-f860ffff(prefetchable) memory:f8620000-f862ffff(prefetchable)

*-network DISABLED     
description: Wireless interface     
physical id: 2    
logical name: wlan0    
serial: 00:24:2b:b1:4b:09     
capabilities: ethernet physical wireless    
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

--------------------------------------------------------------------------------------
john@jsc:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

---------------------------------------------------------------------------------------
john@jsc:/etc/network$ rfkill list

0: dell-wifi: Wireless LAN    
Soft blocked: no 
Hard blocked: no

1: phy0: Wireless LAN   
Soft blocked: no  
Hard blocked: no

--------------------------------------------------------------------------------------

Does anyone have any suggestions?

---

