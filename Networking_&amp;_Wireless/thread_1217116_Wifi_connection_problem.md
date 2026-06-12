---
title: "Wifi connection problem"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by 3.14.TR on 2009-07-19
Hello,
 I am a noob with Ubuntu 9.04. I have got a notebook ACER TravelMate 6593.  
 

 Notebook is connected to internet via T-Mobile 4G Combi PCMCIA card. It works fine with Ubuntu. 

Moreover I want to connect this notebook via integrated WiFi Intel PRO/Wireless 5300 AGN to my home LAN (I mean to the switch ASUS WL-500gPremium, which is configured as a switch and not as a router). I have set WIFi connection easily in MS-Win XP, but I am not able to set it in Ubuntu. In Ubuntu Network Manager, there is my home network (private_net) visible. When I click to private_net, the password dialog is open with the information: „Type of wireless security = WPA&WPA2 Personal“. After entering my net password „kdedomovmuj“, the Network Manager starts to connect for some time-out, but without success. In the Network Manager a new wireless connection is created: Auto private_net with following parameter:
```
  
 SSID: private_netMode: infrastructure
 MTU: automatic
 Security: WPA&WPA2 Personal
 Password: 5e95689b92d316d090f783865a3aaa3a0337a0eddd807e13855e02f25c0312df
 The other parameters are empty.
 
``` Later, I intend to share internet connection of Acer notebook through the switch to other computers. (Again, it works fine in MS-Win XP but not in Ubuntu).
 

 These are parameters of WiFi setting found in MS-Win XP:
 ```

 SSID: private_net
 Net password: kdedomovmuj
 Type of validation: WPAPSK
 Type of encryption: TKIP
 Type of connection ESS
 Connection: automatic
 Physical address: 00-16-EA-ED-F3-D8
 IP: 192.168.0.1
 Subnet mask: 255.255.255.0
 
```
 The result for 2 Ubuntu commands:
 ```

 **sudo lshw -C network**
 *-network  
 description: Ethernet interface  
 product: 82567LM Gigabit Network Connection  
 vendor: Intel Corporation  
 physical id: 19  
 bus info: pci@0000:00:19.0  
 logical name: eth0  
 version: 03  
 serial: 00:1d:72:dd:8d:37  
 capacity: 1GB/s  
 width: 32 bits  
 clock: 33MHz  
 capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
 configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 latency=0 link=no module=e1000e multicast=yes port=twisted pair  
 *-network  
 description: Wireless interface  
 product: PRO/Wireless 5300 AGN [Shiloh] Network Connection  
 vendor: Intel Corporation  
 physical id: 0  
 bus info: pci@0000:03:00.0  
 logical name: wmaster0  
 version: 00  
 serial: 00:16:ea:ed:f3:d8  
 width: 64 bits  
 clock: 33MHz  
 capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless  
 configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn  
 *-network DISABLED  
 description: Ethernet interface  
 physical id: 2  
 logical name: pan0  
 serial: aa:48:8c:d6:aa:cc  
 capabilities: ethernet physical  
 configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 
``` ```
  
 **sudo iwconfig ** 
 lo no wireless extensions.  

 eth0 no wireless extensions.  
  
 wmaster0 no wireless extensions.  
  
 wlan0 IEEE 802.11abgn ESSID:""  
 Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated  
 Tx-Power=14 dBm  
 Retry min limit:7 RTS thr:off Fragment thr=2352 B  
 Encryption key:off  
 Power Management:off  
 Link Quality:0 Signal level:0 Noise level:0  
 Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0  
 Tx excessive retries:0 Invalid misc:0 Missed beacon:0  
 

  pan0 no wireless extensions. 
```  Could anybody help me?

---

### Post by 3.14.TR on 2009-07-22
done with "wicd"

---

