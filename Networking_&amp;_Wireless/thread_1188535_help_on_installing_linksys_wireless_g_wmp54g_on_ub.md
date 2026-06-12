---
title: "help on installing linksys wireless g wmp54g on ubuntu 9.04"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by paradoxart4 on 2009-06-15
To start off i just installed ubuntu 9.04 on my computer less than a week ago so i am completely lost. i bought a linksys wireless-g Model wmp54g ver. 4.1 and it wont install. If anyone knows how to install it i would greatly appreciate the help.

---

### Post by superprash2003 on 2009-06-16
post output of **lshw -C network** from your terminal

---

### Post by paradoxart4 on 2009-06-17
> **superprash2003 said:**
> post output of **lshw -C network** from your terminal

	 	 emasias@emasias-desktop:~$ lshw -c network  
 WARNING: you should run this program as super-user.  
   *-network:0              
        description: Wireless interface  
        product: RT2561/RT61 802.11g PCI 
        vendor: RaLink  
        physical id: 9  
        bus info: pci@0000:00:09.0  
        logical name: wmaster0  
        version: 00  
        serial: 00:23:69:72:5c:9e  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list logical ethernet physical wireless  
        configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg  
   *-network:1  
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: b  
        bus info: pci@0000:00:0b.0  
        logical name: eth0  
        version: 10  
        serial: 00:40:ca:37:1d:57  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes  
   *-network DISABLED  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: 5e:b8:0f:14:4b:84  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes  
 emasias@emasias-desktop:~$

---

### Post by superprash2003 on 2009-06-27
post output of
1) sudo iwconfig
2)sudo iwlist scanning
3)ifconfig

---

