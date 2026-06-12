---
title: "Wireless and Wired Network Not Working"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by Phoenix287 on 2009-09-10
Hi all,

Ubuntu will not currently connect to either a wired network or wireless n or b. I was using a wireless-g network and it was working fine, but I recently moved into a house with both b and n, but can't connect to either network. Today when I tried to plug into a wired network in order to install the necessary upgrades for the wireless, it wouldn't recognize the wired network either. Any suggestions?

---

### Post by Iowan on 2009-09-10
Check **lshw -C network** for information on your interfaces.  **ifconfig -a** should show whether any have an IP address. I presume you're using DHCP - [this]("http://ubuntuforums.org/showthread.php?t=1156441") may not help - but worth checking.

---

### Post by Phoenix287 on 2009-09-11
lshw -c network returns:

	 	 *-network UNCLAIMED      
        description: Ethernet controller  
        product: Attansic Technology Corp.  
        vendor: Attansic Technology Corp.  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        version: c0  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=0  
   *-network  
        description: Wireless interface  
        product: Wireless WiFi Link 5100  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wmaster0  
        version: 00  
        serial: 00:22:fa:05:65:94  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list logical ethernet physical wireless  
        configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn  
   *-network DISABLED 
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: ca:08:f1:a3:3b:83  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes  
 

 
ifconfig -a returns:
	 	 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:692 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:692 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:52528 (52.5 KB)  TX bytes:52528 (52.5 KB)  
 

 pan0      Link encap:Ethernet  HWaddr ca:08:f1:a3:3b:83   
           BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:22:fa:05:65:94   
           inet6 addr: fe80::222:faff:fe05:6594/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:7 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:2004 (2.0 KB)  
 

 wmaster0  Link encap:UNSPEC  HWaddr 00-22-FA-05-65-94-00-00-00-00-00-00-00-00-00-00  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

