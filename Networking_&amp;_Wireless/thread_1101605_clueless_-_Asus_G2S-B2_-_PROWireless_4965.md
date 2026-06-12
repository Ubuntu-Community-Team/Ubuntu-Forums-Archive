---
title: "clueless - Asus G2S-B2 - PRO/Wireless 4965"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by worthspending on 2009-03-20
I have tried suggesting from many sources; googling, forums, wiki, etc. with no luck.  I started over with a fresh install.

Here is my laptop:
Asus G2S-B2
[http://reviews.cnet.com/laptops/asus-g2s-b2-core/4505-3121_7-32780907.html](http://reviews.cnet.com/laptops/asus-g2s-b2-core/4505-3121_7-32780907.html)

Output from several commands:
# lshw -C network
  *-network                                 
       description: Ethernet interface      
       product: L1 Gigabit Ethernet Adapter 
       vendor: Attansic Technology Corp.    
       physical id: 0                       
       bus info: pci@0000:02:00.0           
       logical name: eth0                   
       version: b0                          
       serial: 00:1d:60:ae:34:cb            
       size: 100MB/s                        
       capacity: 1GB/s                      
       width: 64 bits                       
       clock: 33MHz                         
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.1.160 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s                                                                                                                                                           
  *-network DISABLED                                                                                                                                                                
       description: Wireless interface                                                                                                                                              
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection                                                                                                             
       vendor: Intel Corporation                                                                                                                                                    
       physical id: 0                                                                                                                                                               
       bus info: pci@0000:03:00.0                                                                                                                                                   
       logical name: wmaster0                                                                                                                                                       
       version: 61                                                                                                                                                                  
       serial: 00:13:e8:d3:83:59                                                                                                                                                    
       width: 64 bits                                                                                                                                                               
       clock: 33MHz                                                                                                                                                                 
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless                                                                                                  
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn                                                                    
  *-network DISABLED                                                                                                                                                                
       description: Ethernet interface                                                                                                                                              
       physical id: 1                                                                                                                                                               
       logical name: pan0                                                                                                                                                           
       serial: fe:53:fb:ad:56:cb                                                                                                                                                    
       capabilities: ethernet physical                                                                                                                                              
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes                                                                             


# lsmod | grep lag                                                                                                                                       
iwlagn                113668  0                                                                                                                                                     
iwlcore               105540  1 iwlagn                                                                                                                                              
mac80211              253440  2 iwlagn,iwlcore                                                                                                                                      
cfg80211               37136  3 iwlagn,iwlcore,mac80211                                                                                                                             


# iwconfig                                                                                                                                               
lo        no wireless extensions.                                                                                                                                                   

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm                                                    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B             
          Encryption key:off                                                
          Power Management:off                                              
          Link Quality:0  Signal level:0  Noise level:0                     
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0          

pan0      no wireless extensions.

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:ae:34:cb
          inet addr:192.168.1.160  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:542 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:896014 (896.0 KB)  TX bytes:50506 (50.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1000 (1000.0 B)  TX bytes:1000 (1000.0 B)

# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

# uname -a
Linux ducktop 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

Where do I start??

---

