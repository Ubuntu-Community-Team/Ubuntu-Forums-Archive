---
title: "WiFi stopped working after update"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by Saracho on 2010-12-07
Hi,
My netbook is a Sony Vaio vpcm121ax running on Netbook Remix. After I downloaded the recent updates my WiFi connection stopped working. I ran lshw -C metwork and it gave this message:

  	 	 	 	p { margin-bottom: 0.08in; }  WARNING: you should run this program as super-user.  
   *-network UNCLAIMED      
        description: Network controller  
        product: RT3090 Wireless 802.11n 1T/1R PCIe  
        vendor: RaLink  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        version: 00  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=0  
        resources: memory:fe900000-fe90ffff  
   *-network  
        description: Ethernet interface  
        product: JMC260 PCI Express Fast Ethernet Controller  
        vendor: JMicron Technology Corp. 
        physical id: 0.5  
        bus info: pci@0000:02:00.5  
        logical name: eth0  
        version: 02  
        serial: 54:42:49:61:7a:e4  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=jme driverversion=1.0.5 latency=0 multicast=yes  
        resources: irq:27 memory:fe800000-fe803fff ioport:e100(size=128) ioport:e000(size=256)  
 
What should i do to get it working again?

---

