---
title: "Can't change the ESSID of wlan0"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by nottake on 2009-03-23
Hi to all...

I've been trying to get the wireless connection working for 2 days now, but no success so far :(- My wireless card is BCM4318 (Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g (rev 02)) and I followed a tutorial to configure it with Ndiswrapper.

 sudo lshw -C network 
[I]
*-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:2a:e5:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g[/I]

from this i can see that ndiswrapper is the actual driver working. Running iwlist I get a bunch of networks (mine among them):
nottake@nottake-laptop:~$ iwlist wlan0 scanning
wlan0     Scan completed :                     
          Cell 01 - Address: 00:1A:2B:14:40:B1 
                    ESSID:"WLAN_5E"            
                    Protocol:IEEE 802.11g      
                    Mode:Managed               
                    Frequency:2.422 GHz (Channel 3)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:on                                        
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s      
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s     
                              48 Mb/s; 54 Mb/s                               
                    Extra:bcn_int=100                                        
                    Extra:atim=0  

Interface wlan0 is up, and can be seen running ifconfig. Running iwconfig I get this:

wlan0     IEEE 802.11g  **ESSID:off/any**
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ANd the problem comes here: I can't change the essid and i've tried many ways... I read in another post that the key need to be set before being able to change the ESSID, but setting the key doesn't change anything in my case.

I'd really appreciate some help... Does anyone know what's wrong here??? I'm using Kubuntu 8.10 by the way...

Thank u guys

---

