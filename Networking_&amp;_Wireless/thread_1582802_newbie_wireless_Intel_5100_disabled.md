---
title: "newbie: wireless Intel 5100 disabled?"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by judico on 2010-09-27
Recently got a Zareason Teo netbook. Wireless came disabled (huh?). Looking for help enabling it. 

Searching the forums gave hints about info that's needed to solve this, but no direct help.

Using Ubuntu 10.4
Wireless: Intel Wireless WiFi Link 5100

**[COLOR=Blue]iwconfig[/COLOR]**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

**[COLOR=Blue] sudo lshw -C network[/COLOR]**
[sudo] password for loca: 
  *-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c6:d5:da:8c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:fe900000-fe901fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:ad:30:da
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.108 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e000(size=256) memory:e0010000-e0010fff(prefetchable) memory:e0000000-e000ffff(prefetchable) memory:fe800000-fe81ffff(prefetchable)

Clues? Suggestions? Requests for more info?

---

### Post by grahammechanical on 2010-09-27
Does the instruction booklet that came with the netbook make any mention of a key press on the keyboard that will switch the wireless card on? It usually takes several seconds to activate.

Do you have a network icon on the right of the top panel. Right click on it and see if there is a tick mark against both Enable Networking and Enable Wireless.

regards

---

### Post by judico on 2010-09-27
Thanks much @grahammechanical

No network icon, yes button (d'oh). 
Button does seem to turn card on, and thanks for warning about taking seconds.
However it's been Working: Acquiring IP Address (DHCP) for several minutes now. It appears that the wireless is enabled (WiFi Radar detects networks), and I'm trying to connect to an open network (mine). Signal is strong (5 bars), location clear (about 2 feet away).

I tried canceling after 10 minutes earlier, canceling took another 10 then crashed the machine. Now I'm just letting it run.

Guessing I have a network AND card problem at this point? Using a Linksys WRT54GL, no fancy settings. (Other devices don't like it when I secure my network. Sigh.)

---

### Post by judico on 2010-09-27
Ah, had to add an entry to the Wireless Networks. Recognizing the network wasn't enough. Working now.

---

