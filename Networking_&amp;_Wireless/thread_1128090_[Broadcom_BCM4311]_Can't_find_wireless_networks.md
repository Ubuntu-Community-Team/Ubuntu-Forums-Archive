---
title: "[Broadcom BCM4311] Can't find wireless networks"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by The_Bash on 2009-04-17
I'm very new to Ubuntu and Linux in general. I apologize if I haven't put up the right information in this thread.

Summary of my problem:

I recently installed Ubuntu 8.04 on my laptop (HP Pavilion DV5040US). All the hardware is working except for the internal wireless controller (miniPCI). The controller is a Broadcom BCM4311. The controller is recognized and the driver is loaded, but somehow I am not able to find any wireless networks.

The system previously worked on MS Vista. The controller worked fine and connected to the router. Windows is no longer on the system. 

What I've tried:

I installed the wireless-tools. Through iwconfig I discovered that my device was recognized but no driver was being loaded. After that I installed the windows drivers using ndiswrapper. I also blacklisted any interfering drivers. The driver seems to be working but when I scan for wireless networks, nothing is found. I disabled WPA protection on my WIFI but still no results.

Output from various terminal commands to identify the problem:

```
$ lspci -nn 
 
06:02.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02) 
```
 
```
$ iwconfig wlan0 
 
wlan0     IEEE 802.11a  ESSID:off/any   
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated    
          Bit Rate:54 Mb/s   Tx-Power:32 dBm    
          RTS thr:2347 B   Fragment thr:2346 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```
 
```
$ lsmod 
 
bcm43xx               127720  0  
ieee80211softmac       30976  1 bcm43xx 
ieee80211              35528  2 bcm43xx,ieee80211softmac 
ieee80211_crypt         7040  1 ieee80211 
ndiswrapper           192920  0  
usbcore               146412  6 usb_storage,libusual,ndiswrapper,ehci_hcd,ohci_hcd 
  
(not sure if I'ce copied all the relevant modules) 
```
 
```
$ dmesg 
 
[   26.941823] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   27.524719] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[   27.536844] ndiswrapper: using IRQ 22 
[   27.791503] usbcore: registered new interface driver ndiswrapper 
[ 4454.464486] bcm43xx driver 
[ 4454.398427] ieee80211_crypt: registered algorithm 'NULL' 
[ 4454.406241] ieee80211: 802.11 data/management/control stack, git-1.1.13 
[ 4454.406250] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
```
 
```
$ sudo lshw -C network 
 
  *-network:0              
       description: Wireless interface 
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:06:02.0 
       logical name: wlan0 
       version: 02 
       serial: 00:14:a5:6e:10:e6 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11a 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:06:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:0f:b0:c2:15:06 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
```
 
```
$ iwlist scan wlan0 
 
wlan0     No scan results 
```
 
```
$ lsb_release -d 
 
Description:	Ubuntu 8.04.2 
```
 
```
$ unaame -mr 
 
2.6.24-23-generic i686 
```
 
```
$ sudo /etc/init.d/networking restart 
 
 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.wlan0.pid with pid 8858 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/wlan0/00:14:a5:6e:10:e6 
Sending on   LPF/wlan0/00:14:a5:6e:10:e6 
Sending on   Socket/fallback 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/wlan0/00:14:a5:6e:10:e6 
Sending on   LPF/wlan0/00:14:a5:6e:10:e6 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
```

I hope someone can help me sort out this problem. Thanks in advance.

---

### Post by superprash2003 on 2009-04-17
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by The_Bash on 2009-04-18
Before I started out on the above mentioned guide, someone gave me the tip to run 'apt-get update' and 'apt-get upgrade'. Wireless works perfect, even with WPA on.

Like I said, I'm a new at Linux. Classis beginner mistake I presume.

---

