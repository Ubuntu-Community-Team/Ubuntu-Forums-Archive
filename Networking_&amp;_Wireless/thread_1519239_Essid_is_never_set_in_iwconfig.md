---
title: "Essid is never set in iwconfig"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by GimpMaster on 2010-06-27
Hello,

I recently got my Belkin USB wireless adapter working by following some other threads in these forums. Now I would like to connect to my access point.

iwlist scan works great and I can see my AP along with others.

However when I follow the step by step instructions here:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) (How to Networking)

I fail during the DHCP request with no DHCPOFFERS.

My AP is using WEP encryption for now (I've even tried it with open encryption).

The thing that I'm seeing or not seeing is that when I set my essid using

sudo iwconfig wlan0 essid "GimpsHouse"

and then after that do an iwconfig it says off/any.

Here is my iwconfig

> 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:48 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Also my ifconfig

> 
wlan0     Link encap:Ethernet  HWaddr 94:44:52:12:8c:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 94:44:52:12:8c:78  
          inet addr:169.254.5.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


Also my iwlist scan

> 
Cell 02 - Address: 00:24:7B:2D:D9:BA
                    ESSID:"GimpsHouse"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0



The one thing that seems suspicious is that iwconfig doesn't set the ESSID, however I can change the channel and watch the frequency change in iwconfig output. Also I get this when issuing sudo ifconfig wlan0 up

dmesg:  ADDRCONF(NETDEV_UP): wlan0: link is not ready


Any thoughts or suggestions is greatly appreciated!

Thanks

---

### Post by GimpMaster on 2010-06-29
Any thoughts? SHould I see iwconfig immediately update the Access Point?

Thanks

---

### Post by chkneater on 2010-07-01
What threads/steps did you use to get your card working?  What version of ubuntu are you using?

---

### Post by GregIthaca on 2011-01-20
I have the same issue.  Most of the threads I have seen, people just give up and try a different card.  No idea why that should be necessary.
I can get iwconfig to set the encryption key but it won't touch the channel or the essid, they always show as 2.462GHz and off/any.

My card is DLink DWL-G120, which was reported to work well back in 2006 and 6.06.  I'm running 8.04LTS.

Greg

---

