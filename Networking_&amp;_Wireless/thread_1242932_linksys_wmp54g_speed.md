---
title: "linksys wmp54g speed"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by acutshall1 on 2009-08-17
I have tried for about a week to get nic card speed to work correctly; it is currently 1.5 Mbps on a 25Mbps network. I'm using  wicd with a script  "sudo iwconfig wlan0 rate 54M" with not success. Before I resort to a ndis wrapper I would like to make sure I am using the correct driver and that there is nothing else I can try. Below is the info for my current configuration. Does anyone have possible solutions for me to try? I see what seems to be mutiple drivers listed below, m i using multple drivers or the wrong one? Am I using the wrong one?

Thanks

*-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:03:0d.0
       logical name: wmaster0
       version: 01
       serial: 00:23:69:d8:d0:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.9 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg


acutshall@mediabox1:~$ lsmod | grep rt2500
rt2500pci              23936  0 
rt2x00pci              15616  1 rt2500pci
rt2x00lib              37888  2 rt2500pci,rt2x00pci
eeprom_93cx6           10240  1 rt2500pci

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"6TJQE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:D2:68:4D:7E   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

