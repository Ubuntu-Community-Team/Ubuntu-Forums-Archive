---
title: "Asus Zenbook Wireless Issues"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by webberdar on 2012-04-03
Hey Everyone,

I recently got myself an Asus zenbook (UX31). After reading this: [https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook), I installed 12.04 and worked through most of the issues successfully. But, I still cant get wireless to work.

Ive tried all of the suggestions on the help.ubuntu site above and also worked through the suggestions here: [http://ubuntuforums.org/showthread.php?t=1857808](http://ubuntuforums.org/showthread.php?t=1857808) but to no avail. I should also note that I can connect to wireless if I am within a meter or so of the router, any further and it wont work, but a friends laptop is getting perfect wireless from anywhere in the house. Any help on this would be much appreciated.

Below is some outputs that may be useful. 

```
darcy@darcy-asus:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux darcy-asus 3.2.0-21-generic #34-Ubuntu SMP Fri Mar 30 04:25:35 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
darcy@darcy-asus:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
``````
darcy@darcy-asus:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
``````
darcy@darcy-asus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 9c:eb:e8:04:e1:85  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9eeb:e8ff:fe04:e185/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1821023 (1.8 MB)  TX bytes:342568 (342.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138395 (138.3 KB)  TX bytes:138395 (138.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:ca:e7:52:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``````

darcy@darcy-asus:~$ lsmod | grep ath
ath3k                  12961  0 
bluetooth             180104  24 rfcomm,bnep,ath3k,btusb
ath9k                 130867  0 
mac80211              519691  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              390898  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              209962  3 ath9k,mac80211,ath
compat                 13135  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
```Thank you in advance.

---

### Post by darakilinc on 2012-04-15
Hello, I also bought a Asus Zenbook just yesterday. And switch the OS from windows to Ubuntu (12.04). And having same problem. Even the router is 2 mt close to my pc, it's connected only 2 ticks out of 5... Is there any way to make the wireless connection better?

---

