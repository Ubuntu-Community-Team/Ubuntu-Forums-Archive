---
title: "Need help with wireless network problem"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by beaverjrgonzalez on 2009-12-02
First a little history. I used to access the INTERNET via DSL, but the dishonesty of my ISP led me to cancel my account. From that point on, I relied on the wireless networks of my local library and/or the wi-fi network of Panera Brea. They work fine.

A counple of weeks ago when I was working on my word processor off-line at home I noticed that a wireless connection named 'NETGEAR" showed up under my network icon. I tried it, and it worked, although a bit slow when it went below 10%. I used it for a couple of weeks.

Then, all of a sudden it stopped working.

It still shows up under the network icon with the following message: "Wireless network connection 'NETGEAR' active: NETGEAR (20%).

When I try to use any of the bookmarks on my Firefox browser all come up as 'NOT FOUND'. I have not made any changes to Firefox.

I tried the UBUNTU documentation and found the following:

  	 	 	 	 	 	  **Check for driver**

 
[LIST=1]
[*]Open a **Terminal** (Applications &#8594; 	Accessories &#8594; Terminal) and type the command: sudo lshw -C 	network
[*]If there is a driver listed then see [the 	section called “Check device is on”]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-disabled").
[*]Set up NDISWrapper ([the 	section called “Using Windows Wireless Drivers”]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html")).
[/LIST]

I ran the command of #2 and here are the results:

  	 	 	 	 	 	  Information Displayed after executing the sudo command:
 


 jorge@ubuntu:~$ sudo lshw -C network  
 


   *-network                
        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 01  
        serial: 00:16:d3:52:94:25  
        size: 10MB/s  
        capacity: 1GB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s  
 


   *-network  
        description: Wireless interface  
        product: AR2413 802.11bg NIC  
        vendor: Atheros Communications Inc.  
        physical id: 5  
        bus info: pci@0000:0a:05.0  
        logical name: wifi0  
        version: 01  
        serial: 00:19:7d:ac:f0:6a  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list logical ethernet physical wireless  
        configuration: broadcast=yes driver=ath_pci ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g  
 


   *-network DISABLED  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: 1e:2b:42:12:e7:1d  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes  
 

 This is all Chinese to me. Can someone help me to see if I can get connected to NETGEAR when it shows up on my network icon?

Any help will be greatly appreciated!   :p:p:p:p

Jorge

---

