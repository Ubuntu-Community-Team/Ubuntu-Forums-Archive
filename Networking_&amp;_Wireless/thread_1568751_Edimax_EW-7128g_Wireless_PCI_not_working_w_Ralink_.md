---
title: "Edimax EW-7128g Wireless PCI not working w/ Ralink RT2561/RT61 Chipset"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by rmink on 2010-09-05
Just installed Ubuntu Studio 10.04 and everything seems to be working nicely except I have no networking.
 
The card does not appear in the Network Settings GUI. The only 3 tabs I have are General, DNS, and Hosts.
 
A screen grab is attached.
 
I'm a long time Windows user trying out some of the best Linux creative apps I can find. So, Ubuntu Studio was a no brainer.
I checked the manufacturer's site for linux drivers and they are available, but I don't know how current. (Edimax site, not RaLink's site.) I opened the file and it looks like it needs to be compiled and installed to work. Something I know almost nothing about. The card is listed as supported in this forum for Ubuntu 9x but I can't find information about it for 10.04
 
Any help would be greatly appreciated.
 
PS. I have no networking on the system but I can transfer files via USB flash drives if needed.
 
Some System info:
```
 
1 ) Machine Brand and Model (PC/Laptop):
Dell Precision 650
 
2 ) Wireless Brand, Model and Wireless Chipset:
03:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI
 
3 ) check interface:
robert@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17388 (17.3 KB)  TX bytes:17388 (17.3 KB)
robert@ubuntu:~$ iwconfig
lo        no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
 
4 ) Check for modules:
robert@ubuntu:~$ lsmod |grep 'rt61'
rt61pci                18920  0 
crc_itu_t               1371  1 rt61pci
rt2x00pci               5995  1 rt61pci
rt2x00lib              27509  2 rt61pci,rt2x00pci
eeprom_93cx6            1333  1 rt61pci
 
5 ) Kernel boot messages
robert@ubuntu:~$ dmesg | grep 'rt61'
[   16.277047] rt61pci 0000:03:0c.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[   16.449502] Registered led device: rt61pci-phy0::radio
[   16.449568] Registered led device: rt61pci-phy0::assoc
 
6 ) Network configuration
robert@ubuntu:~$ sudo lshw -C network
[sudo] password for robert: 
  *-network DISABLED      
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: c
       bus info: pci@0000:03:0c.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:1d:3d:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:25 memory:fe5f8000-fe5fffff
 
7 ) Scan for networks:
robert@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.
wlan0     Failed to read scan data : Network is down
 
8 ) Ubuntu Version:
robert@ubuntu:~$ lsb_release -d
Description: Ubuntu 10.04 LTS
 
9 ) Kernel/architecture (including 32 vs. 64 bit):
robert@ubuntu:~$ uname -mr
2.6.32-21-generic i686
 
10 ) Restarting the network:
robert@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...     
 

```

---

### Post by rmink on 2010-09-08
Bump.

Still stuck without networking when in Linux.

---

