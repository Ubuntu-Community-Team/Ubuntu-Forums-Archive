---
title: "Wireless coneptronic C54Ri on ubuntu 11.10"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by jrosell on 2011-11-09
New install on ubuntu 11.10 using coneptronic C54Ri.

As documentation says it uses Ralink drivers....

$ lspci -nn | grep -i 'ralink'
01:05.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:90:e5:af:13  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fee5:af13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39812172 (39.8 MB)  TX bytes:1633405 (1.6 MB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6608 (6.6 KB)  TX bytes:6608 (6.6 KB)



$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


$ lsmod | grep rt
rt61pci                27493  0 
crc_itu_t              12627  1 rt61pci
rt2x00pci              14202  1 rt61pci
rt2x00lib              48114  2 rt61pci,rt2x00pci
mac80211              272785  2 rt2x00pci,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt61pci
parport_pc             32114  1 
parport                40930  3 ppdev,parport_pc,lp

$ lsmod | grep rt
[ 2497.816989] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access 
failed: offset=0x0000308c, value=0xffffffff
[ 2497.827112] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access 
failed: offset=0x0000308c, value=0xffffffff
[ 2497.837430] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access 
failed: offset=0x0000308c, value=0xffffffff
[ 2497.847528] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access 
failed: offset=0x0000308c, value=0xffffffff
[ 2497.847632] phy0 -> rt61pci_wait_bbp_ready: Error - BBP register access faile
d, aborting.
[ 2497.847637] phy0 -> rt61pci_set_device_state: Error - Device failed to enter 
state 4 (-5).



sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: Ralink corp.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wlan0
       version: 00
       serial: fa:b8:14:58:62:35
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=3.0.0-12-generic firmware=0.8 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:fdef8000-fdefffff



$  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down



$ uname -mr
3.0.0-12-generic i686

---

