---
title: "Wifi Issues slow, dropping, can not connect DYI comp"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by hjfarnsworth on 2010-06-11
TY for any help you can give me, I have been working on this for about 6  hours now with no luck. 


[LIST]
[*][COLOR=Black]Intel Core i3-530 Clarkdale 2.93GHz[/COLOR]
[*][COLOR=Black]Gigabyte GA-H55M-USB3 Motherboard[/COLOR]
[*][COLOR=Black]4 GB DDR3 1333 RAM (2 x 2GB)[/COLOR]
[*][COLOR=Black]Rosewill RNX-G300LX pci wifi card[/COLOR]
[*][COLOR=Black]Ubuntu 10.4 32 bit
[/COLOR]
[/LIST]
I looked around and found people saying that the  RNX-g300 would work out of box with ubuntu which is good because all i  have is wifi. 

It seems to be hit or miss right now some times wifi works great, other  times wifi Disconnects every min or can not connect at all. 

The internet moves slow actually it is faster on my 500mhz 200mb ram  windows laptop!

I have tried every thing from adjusting firefox to changing system  settings per what other posts and blogs have said. None of them really  seem to work. 

I followed the directions best i could from teh sticky hope this helps. 

PS i am a complete Linux Noob so feel free to over explain if needed :-)

**Wireless Brand, Model and Wireless Chipset:**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
05:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI


** check interface:**

wlan0     IEEE 802.11bg  ESSID:"Pippi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:  00:1F:33:C9:B3:E4   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off    Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




** Network configuration**
*-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 00
       serial: 00:1a:ef:07:90:31
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=172.16.0.6  latency=32 multicast=yes wireless=IEEE 802.11bg

** Scan for networks:**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

**Kernel/architecture (including 32 vs. 64 bit): **
2.6.32-22-generic-pae i686

**Restarting the network:**
 * Reconfiguring network interfaces...                                                                  [ OK ]

---

