---
title: "WIFI cannot be found"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by aryangor on 2010-06-07
Hello!

I am using Ubuntu Karmic. For the past 6 months I could pick up the WiFi spot in our house, until last weekend when it just disappeared from my network manager. Everyone else in my house can see the WiFi and connect, even the Karmic users - only me has nothing! I can see our neighbors' WiFi though - I could always see it, so I don't think the problem is with my hardware.

I tried to reinstall the connection via network manager - did not work. I reinstalled Karmic - no effect. I tried Lucid - nothing!! It just disappeared! I had connection 3 days ago, but now I don't know what to do.

Any help will be appreciated. Do you need to see any output here?

---

### Post by aryangor on 2010-06-08
**OUTPUT : lshw -c network                                     **
  *-network                                                                  
       description: Wireless interface                                       
       product: PRO/Wireless 3945ABG [Golan] Network Connection              
       vendor: Intel Corporation                                             
       physical id: 0                                                        
       bus info: pci@0000:06:00.0                                            
       logical name: wmaster0                                                
       version: 02                                                           
       serial: 00:13:02:34:a2:95                                             
       width: 32 bits                                                        
       clock: 33MHz                                                          
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:84000000-84000fff                                                 
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:07:83:bd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.250 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:d2006000-d2006fff ioport:2000(size=64)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

====================================================

**OUTPUT : dmesg | grep wl **
                                                                         
[   35.125552] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   35.125557] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   35.125700] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   35.125716] iwl3945 0000:06:00.0: setting latency timer to 64
[   35.196925] iwl3945 0000:06:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   35.196930] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   35.197093] iwl3945 0000:06:00.0: irq 28 for MSI/MSI-X
[   35.300922] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   36.124392] iwl3945 0000:06:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   36.168618] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
[   36.237090] Registered led device: iwl-phy0::radio
[   36.237115] Registered led device: iwl-phy0::assoc
[   36.237174] Registered led device: iwl-phy0::RX
[   36.237199] Registered led device: iwl-phy0::TX

===================================================

dmesg | grep wlan0

NO OUTPUT

---

