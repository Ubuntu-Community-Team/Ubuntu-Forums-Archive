---
title: "Gigabyte wireless card UNCLAIMED"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by wa2due on 2010-01-23
don@don-laptop:~$ sudo lshw -C network  
   *-network                
        description: Ethernet interface  
        product: 3c905C-TX/TX-M [Tornado]  
        vendor: 3Com Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 78  
        serial: 00:08:74:e2:e1:20  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s  
        resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:28000000-2801ffff(prefetchable)  
   *-network UNCLAIMED  
        description: Network controller  
        product: RT2500 802.11g Cardbus/mini-PCI  
        vendor: RaLink  
        physical id: 1  
        bus info: pci@0000:03:00.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm cap_list  
        configuration: latency=0  
        resources: memory:f4000000-f4001fff  
 don@don-laptop:~$  
 

 How do I get Ubuntu to CLAIM the wireless network?
 

 This is Ubuntu 9.10 running on a Dell Inspiron 8200 laptop.  I was told that this wireless card was Linux compatible and that the driver was included in Ubuntu 9.10.
 Please help this 85 year old newbie.

---

### Post by chili555 on 2010-01-23
This 66 year old whipper-snapper is here to help. We'd love to know exactly which Ralink RT2500 you have. Please do:```
  	
lspci -n | grep 03:00
```Just as an experiment, to see if we can get it going by dead reckoning, let's try:```
sudo modprobe rt2500pci
iwconfig
```Do you now have a wireless interface? If not, please post:```
dmesg | grep rt25
```Thanks.

---

