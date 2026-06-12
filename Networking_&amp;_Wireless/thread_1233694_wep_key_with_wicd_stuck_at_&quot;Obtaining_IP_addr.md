---
title: "wep key with wicd stuck at &quot;Obtaining IP address&quot;"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by methodbud on 2009-08-07
[FONT=Arial][SIZE=2]Hi,[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]I’m a new user of Ubuntu 9.04 and I’ve been trying to connect to my router with my wifi Linksys WMP11v4 for a few days.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]I installed the drivers with ndiswrapper and installed wicd. The problem is with the WEP key. If I remove security on the router, I can connect. So, I assume the drivers are ok.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]When I try to connect with wicd, at the bottom of the window, I can read “Valid autentification” followed by “Obtaining IP address”. Then it keeps on trying to “Obtain the IP address” for a while until I get “Not Connected”.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]I tried with no success, to change the WEP key in the xxxx-xxxx-xx format as I read in a thread on this forum.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]I also tried every option in the wicd / preferences / WPA Supplicant Driver. It’s only with “wext” that I get the “Obtaining IP address” otherwise “Not Connected” comes very quick.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]Here is my lshw –C network[/SIZE][/FONT]
  
  [FONT=Arial]  *-network DISABLED
       description: Wireless interface
       product: WMP11v4 802.11b PCI card
       vendor: Linksys, A Division of Cisco Systems
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: wlan0
       version: 00
       serial: 00:0f:66:95:d6:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper&#38600;&#43421; driverversion=1.53&#2603;Linksys, LLC.,08/15/2 latency=64 maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:cb:0d:c1:81:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
 [/FONT]
                   
  [FONT=Arial]Thanks for your help.[/FONT]

---

### Post by methodbud on 2009-08-07
I tried to manualy configure my connection using this thread
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

When I did the : 
sudo iwconfig <interface> key HEX_KEY
I tried all different ways to enter HEX_KEY with "HEX_KEY", capitals... and I always get  the following message : 

Error for wireless request "set encode" (8B2A) : Set failed on device wlan0 ; Invalid Argument.

Now I'm desperate.

---

