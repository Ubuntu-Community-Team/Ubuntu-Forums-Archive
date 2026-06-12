---
title: "Wireless not working (Interfaces file issues?)"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by Agent_Riot on 2012-06-19
When my computer boots it mentions that it is trying to autoconfigure the network. This always fails. Inside the OS I can use commands like iwconfig wlan0 and it shows me info about my wireless card. It's even listed in System Information (hardinfo) but the system acts as if I have no network. I can't access it at all. Typing PING 8.8.8.8 gets me "CONNECT: network is unreachable"

I ran some commands to try and get more info.

                                  Results of iwconfig:
 

 lo        no wireless extensions.  
 

 wlan0     IEEE 802.11abg  ESSID:ff/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr:ff   Fragment thr:ff  
           Power Management:ff  
            
 eth0      no wireless extensions.  
 

 Results of ifconfig:
 

 wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:ce:f6:84   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 From lspci:
 

 0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)  
 

 from sudo lshw -c -network (From live CD terminal, as my GUI is having issues/crashing)
 

   *-network                
        description: Wireless interface 
        product: PRO/Wireless 3945ABG [Golan] Network Connection 
        vendor: Intel Corporation 
        physical id: 0 
        bus info: pci@0000:0c:00.0 
        logical name: wlan0 
        version: 02 
        serial: 00:1f:3c:ce:f6:84 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-23-generic firmware=15.32.2.9 ip=23.2.5.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg 
        resources: irq:46 memory:f6cff000-f6cfffff 
   *-network 
        description: Ethernet interface 
        product: NetLink BCM5906M Fast Ethernet PCI Express 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:09:00.0 
        logical name: eth0 
        version: 02 
        serial: 00:23:ae:29:09:ed 
        capacity: 100Mbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair 
        resources: irq:48 memory:f69f0000-f69fffff 
  
I checked the interfaces file because some people online say it is used to get settings. It only says two lines - "Auto wlan0" and then "Auto eth0". I don't think that's right.

Any ideas on the issue. I'm on the Live CD right now using the Wifi fine. But in the HD's OS it's borked.

---

