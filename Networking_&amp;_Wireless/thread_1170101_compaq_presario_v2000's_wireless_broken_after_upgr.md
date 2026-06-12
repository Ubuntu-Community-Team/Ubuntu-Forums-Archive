---
title: "compaq presario v2000's wireless broken after upgrade to 9.04"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by usaar33 on 2009-05-25
Hello,
  I've been happily using my presario v2000 with kubuntu for some time now.  Unfortunately, after upgrading to 9.04, the wireless stopped working correctly.

Specifically:
-The wifi indicator (toggle switch on laptop) keeps blinking on and off.  Before it never showed.
-iwlist scan will only show APs after turning the wireless on (from off) by hitting the button.  After that, no new scans occur. (so after 10 seconds, the old scans timeout and I see nothing with iwlist scan)
-I cannot connect to any network, even unsecure ones.

The card (Intel 2200BG) is clearly being detected correctly, but it is completely unusable.

Any advice on how to restore wifi connectivity?

---

### Post by superprash2003 on 2009-05-26
post output of **lshw -C network** from the terminal

---

### Post by usaar33 on 2009-05-26
As requested:

  *-network:0                                           
       description: Ethernet interface                  
       product: RTL-8139/8139C/8139C+                   
       vendor: Realtek Semiconductor Co., Ltd.          
       physical id: 0                                   
       bus info: pci@0000:02:00.0                       
       logical name: eth2                               
       version: 10                                      
       serial: 00:c0:9f:69:0f:8b                        
       size: 100MB/s                                    
       capacity: 100MB/s                                
       width: 32 bits                                   
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.105 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:69:31:4d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:91:f4:ce:33:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by usaar33 on 2009-05-28
any ideas?

---

