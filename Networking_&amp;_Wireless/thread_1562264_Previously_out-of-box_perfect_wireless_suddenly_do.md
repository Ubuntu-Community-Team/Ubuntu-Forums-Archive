---
title: "Previously out-of-box perfect wireless suddenly doesn't work"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by Pangthagerous on 2010-08-27
This is my first post on this forum.
I have been using ubuntu for about a year and a half. Up until yesterday, my new laptop's wifi worked perfectly out of the box with Ubuntu 10.04. I am dual-booting Windows 7 and Ubuntu 10.04. I was in Windows yesterday afternoon and restarted to boot into Ubuntu, and found that the wifi was not working and I could not manually turn it off and on with the wifi button on the laptop. I don't even know where to start because I was so used to relying on bcmwl-kernel-source for my wifi driver on my previous laptop, and this does not require it. 

relevant system specs: 
Acer Aspire 5534 
AMD Athlon 64 X2 processor (running Ubuntu 10.04 64-bit)
Acer Nplify 802.11b/g/Draft-N

Sorry if this is more information than necessary and/or missing something important.


= = = = =
Mörgæs 2013-12-05:
Using Lubuntu 13.10 everything works in first attempt.

---

### Post by bkratz on 2010-08-27
> **Pangthagerous said:**
> This is my first post on this forum.
I have been using ubuntu for about a year and a half. Up until yesterday, my new laptop's wifi worked perfectly out of the box with Ubuntu 10.04. I am dual-booting Windows 7 and Ubuntu 10.04. I was in Windows yesterday afternoon and restarted to boot into Ubuntu, and found that the wifi was not working and I could not manually turn it off and on with the wifi button on the laptop. I don't even know where to start because I was so used to relying on bcmwl-kernel-source for my wifi driver on my previous laptop, and this does not require it. 

relevant system specs: 
Acer Aspire 5534 
AMD Athlon 64 X2 processor (running Ubuntu 10.04 64-bit)
Acer Nplify 802.11b/g/Draft-N

Sorry if this is more information than necessary and/or missing something important.

Since you were last using Windows, there have been postings that showed that Windows sometimes locks up the wireless especially if you don't shut down properly.  It is worth a try to reboot into windows, try it and do another shutdowm.

---

### Post by Pangthagerous on 2010-08-27
I tried a proper shutdown of Windows then booting into Ubuntu, no change.

---

### Post by Pangthagerous on 2010-08-28
Here is the output of the commands from the thread about proper procedures for getting help. As of right now, the wireless works fine in Windows and does not work at all in Ubuntu
```

pang@pang-laptop:~$ lspci
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01) 

pang@pang-laptop:~$ ifconfig
lo        Link encap:Local Loopback          
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:1994 errors:0 dropped:0 overruns:0 frame:0 TX packets:1994 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:289209 (289.2 KB)  TX bytes:289209 (289.2 KB)

pang@pang-laptop:~$ iwconfig wlan0 
wlan0     IEEE 802.11bgn  ESSID:off/any             
Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm              
Retry  long limit:7   RTS thr:off   Fragment thr:off           
Power Management:off 

pang@pang-laptop:~$ lsmod | grep "ath9k" ath9k                 
328989  0  mac80211              
238448  1 ath9k ath                     
9723  1 ath9k cfg80211              
148546  3 ath9k,mac80211,ath led_class               
3764  1 ath9k 

pang@pang-laptop:~$ dmesg | grep "ath9k" 
[   18.610480] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   18.610495] ath9k 0000:02:00.0: setting latency timer to 64 
[   19.117299] phy0: Selected rate control algorithm 'ath9k_rate_control' 
[   19.118589] Registered led device: ath9k-phy0::radio 
[   19.118621] Registered led device: ath9k-phy0::assoc 
[   19.118664] Registered led device: ath9k-phy0::tx 
[   19.118701] Registered led device: ath9k-phy0::rx 

pang@pang-laptop:~$ sudo lshw -C network [sudo] password for pang:   
 *-network DISABLED              
description: Wireless interface        
product: AR928X Wireless Network Adapter (PCI-Express)        
vendor: Atheros Communications Inc.        
physical id: 0        
bus info: pci@0000:02:00.0        
logical name: wlan0        
version: 01        
serial: 0c:60:76:4c:6c:75        
width: 64 bits        
clock: 33MHz        
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn        
resources: irq:16 memory:f1100000-f110ffff   
*-network DISABLED        
description: Ethernet interface        
product: RTL8111/8168B PCI Express Gigabit Ethernet controller        
vendor: Realtek Semiconductor Co., Ltd.        
physical id: 0        
bus info: pci@0000:08:00.0        
logical name: eth0        
version: 02
 serial: 00:26:22:24:8c:66        
size: 10MB/s        
capacity: 1GB/s        
width: 64 bits        
clock: 33MHz        
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 
1000bt 1000bt-fd autonegotiation        
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 
link=yes multicast=yes port=MII speed=10MB/s        
resources: irq:27 ioport:2000(size=256) memory:f1010000-f1010fff(prefetchable) memory:f1000000-f100ffff(prefetchable) memory:f1020000-f102ffff(prefetchable)
       
pang@pang-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning.  
eth0      Interface doesn't support scanning.  
wlan0     Failed to read scan data : Network is down 

pang@pang-laptop:~$ lsb_release -d 
Description:    Ubuntu 10.04.1 LTS 

pang@pang-laptop:~$ uname -mr 
2.6.32-24-generic x86_64 

pang@pang-laptop:~$ sudo /etc/init.d/networking restart  
* Reconfiguring network interfaces...                                   [ OK ]
```

---

