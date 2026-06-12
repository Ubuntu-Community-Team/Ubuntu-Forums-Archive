---
title: "WPA-2 Personal wifi, Atheros"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by hoopsterj2 on 2009-12-10
I installed Ubuntu 9.10 onto Dell Latitude Cpx Laptop. I can get online w/ a neighbor w/out security, but when I set my own up, it isn't listed.
 My router set up: WPA2 security, SSID Broadcast disabled, auto channel AES PSK, passphrase.
 Linux compatibility info: Airplus 101, AWLH403 Atheros (driver: madwifi) Works out of the box in Breezy via the madwifi linux-restricted-kernel that is included by default. No tweaking required. 2005-09-29  (this works fine w/ Win2k; ubuntu reads the Airplus driver cd, and can pull up cvn3ab.inf, but I don't know whether that is needed in this scenario – i've installed the n***wrapper package just in case).
                                  commands produce:
 06:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
 

 wlan0 IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated    
  Tx-Power=27 dBm    
  Retry  long limit:7   RTS thr:off   Fragment thr:off
  Power Management:off
 
Retry  long limit:7   RTS thr:off   Fragment thr:off
  Power Management:off
 

 ath5k                 121988  0  
  mac80211              210408  1 ath5k
  ath                     8444  1 ath5k
  cfg80211              130440  3 ath5k,mac80211,ath
  30.034358] ath5k 0000:06:00.0: enabling device (0000 -> 0002)
   

iwlist scan
  lo        Interface doesn't support scanning.
    wlan0     Scan completed :
  Cell 01 - Address: 00:1D:7E:90:0D:B5
Channel:11
                                    Frequency:2.462 GHz (Channel 11)
  Quality=29/70  Signal level=-81 dBm   
  Encryption key:off
  ESSID:"jimshouse"
  Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
  Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
  36 Mb/s; 48 Mb/s; 54 Mb/s
    Mode:Master
Extra:tsf=00000629107ee714
  Extra: Last beacon: 22260ms ago
  IE: Unknown: 00096A696D73686F757365
  IE: Unknown: 010482848B96
  IE: Unknown: 03010B
  IE: Unknown: 2A0104
  IE: Unknown: 32080C1218243048606C
  IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
  IE: Unknown: DD07000C4301000000
    eth1      Interface doesn't support scanning.
   2.6.31-16-generic i686
 ath5k                 121988  0  
  mac80211              210408  1 ath5k
  ath                     8444  1 ath5k
  cfg80211              130440  3 ath5k,mac80211,ath
  led_class               4096  1 ath5k
 

  eth1      Link encap:Ethernet  HWaddr 00:10:a4:a4:6b:ac   
  Inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
  inet6 addr: fe80::210:a4ff:fea4:6bac/64 Scope:Link
  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  RX packets:3409 errors:0 dropped:0 overruns:0 frame:0
  TX packets:3000 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:1000  
  RX bytes:3619799 (3.6 MB)  TX bytes:357534 (357.5 KB)
  Interrupt:11 Base address:0x1000  
 

   lo        Link encap:Local Loopback   
  inet addr:127.0.0.1  Mask:255.0.0.0
  inet6 addr: ::1/128 Scope:Host
  UP LOOPBACK RUNNING  MTU:16436  Metric:1
  RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:0  
  RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
    wlan0     Link encap:Ethernet  HWaddr 00:0f:a3:26:d6:50   
  inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
  inet6 addr: fe80::20f:a3ff:fe26:d650/64 Scope:Link
  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  RX packets:2 errors:0 dropped:0 overruns:0 frame:0
  TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:1000  
  RX bytes:1180 (1.1 KB)  TX bytes:5773 (5.7 KB)

---

### Post by iconoclast hero on 2011-03-29
Just as a side note, AT&T Plug&Share 6500g which is an AR5001x+ Atheros Rev 01 works with WPA2-AES on 10.10 server.

```
             IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

---

### Post by romain.astie on 2012-02-03
Looks as if I'm having the same problem as you are... My connection icon keeps on spinning after I've pressed the connect button and entered my password. I also have a Dell, but the CPi, not CPx... Let's see if we can get this problem solved! Also, the output for the network I need to connect to is the same:```

Cell 02 - Address: E0:46:9A:68:38:5A ESSID:"i-Sails"
Protocol:IEEE 802.11b Mode:Managed Frequency:2.437 GHz (Channel 6) Quality:40/100 Signal level:-70 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100 Extra:atim=0
 IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP Pairwise Ciphers (1) : CCMP Authentication Suites (1) : PSK
```

---

### Post by Iowan on 2012-02-03
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
10 months is old enough. I notice you already have a [thread]("http://ubuntuforums.org/showthread.php?t=1918760") started.

---

