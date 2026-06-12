---
title: "Dell Wireless Laptop issues"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by nortonte on 2009-11-19
Hi, another newbie here.

I have a Dell with a 1390 WLAN Minicard installed. Works fine with Windows.

I have disabled the wired connection, but don't have a clue on completing the wireless connection.

Here are the details:

  	 	 	 	 	 	  *-network                
        description: Network controller  
        product: BCM4311 802.11b/g WLAN  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:0b:00.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: driver=b43-pci-bridge latency=0  
        resources: irq:16 memory:efdfc000-efdfffff  
   *-network  
        description: Ethernet interface  
        product: BCM4401-B0 100Base-TX  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth0  
        version: 02  
        serial: 00:15:c5:cd:4d:5f  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes  
        resources: irq:17 memory:ef9fe000-ef9fffff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:0e:a6:f4:7e:1e  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 



Any help would be appreciated.

---

