---
title: "my wireless stopped working"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by nikonfrz on 2009-04-23
my wireless worked fine until two days ago. i haven't done any updates or anything. i can log into my router and modem(while wired) and access everything but not while trying to wireless. any thoughts?

---

### Post by t0mppa on 2009-04-23
Really hard to say anything without some more information on your system. Open up a terminal, run these commands one by one and post the results: ```
lspci
iwconfig
lshw -C network
iwlist scan
```

---

### Post by nikonfrz on 2009-04-23
sorry i know. but i'm still a newb and didn't know what info was needed!

```
root@vpkeebs-laptop:/home/vpkeebs# lscpi
bash: lscpi: command not found
root@vpkeebs-laptop:/home/vpkeebs# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"dlink"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:17:9A:35:41:54   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6A64-7562-6B   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@vpkeebs-laptop:/home/vpkeebs# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 20
       serial: 00:02:3f:25:01:76
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.100 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:0b:ee:d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:b4:fe:0e:ef:c6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@vpkeebs-laptop:/home/vpkeebs# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1F:B3:AC:E7:21
                    ESSID:"2WIRE746"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-44 dBm  
                    Extra: Last beacon: 212ms ago
          Cell 02 - Address: 00:23:75:08:0A:90
                    ESSID:"qwest6624"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    Extra: Last beacon: 148ms ago
          Cell 03 - Address: 00:1F:B3:B1:48:A1
                    ESSID:"2WIRE053"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    Extra: Last beacon: 408ms ago
          Cell 04 - Address: 00:14:6C:FB:86:82
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=70/100  Signal level=-58 dBm  
                    Extra: Last beacon: 1020ms ago
          Cell 05 - Address: 00:1B:2F:DF:E7:46
                    ESSID:"Netgear 4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 6296ms ago
          Cell 06 - Address: 00:15:05:9F:92:F4
                    ESSID:"myqwest7845"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    Extra: Last beacon: 488ms ago
          Cell 07 - Address: 00:1D:7E:3B:FB:64
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    Extra: Last beacon: 484ms ago
          Cell 08 - Address: 00:22:6B:07:47:2C
                    ESSID:"@Home472C"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    Extra: Last beacon: 7636ms ago
          Cell 09 - Address: 00:17:9A:35:41:54
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-46 dBm  
                    Extra: Last beacon: 100ms ago
          Cell 10 - Address: 00:22:3F:D7:DA:A6
                    ESSID:"YOUR-6B11988A43-Wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 24ms ago

pan0      Interface doesn't support scanning.

root@vpkeebs-laptop:/home/vpkeebs# 
```

---

### Post by t0mppa on 2009-04-23
Well, there is a help post about what info to include in your help request, but it's buried inside the other sticky thread, so not too many posters end up reading it.

Anyhow, which part of your wireless doesn't work then? Looks like it's able to scan and detect wireless networks around it normally. Is it not finding your own routers network or just can't connect to any of the networks it finds?

---

### Post by lisati on 2009-04-23
There seem to be more than one network using channel 6. If one of them is yours, I'd suggest changing the channel number, to help avoid the possibility of a conflict. I was experiencing intermittent trouble connecting wirelessly to one of my routers, when I noticed that a neighbour seemed to be using the same channel for theirs - changing mine seemed to help.

---

### Post by t0mppa on 2009-04-23
Actually, I this iwconfig part shows what's the trouble: ```
eth1      unassociated  ESSID:"dlink"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:17:9A:35:41:54   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6A64-7562-6B   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

No wireless protocol associated; power management, etc. are off. Are you sure you haven't just turned your wireless off with a button or a key combination? Found a post with exactly the same kind of problem (equal iwconfig output), where the user had just accidently pressed Fn + F2 on his laptop and turned the device off.

---

### Post by nikonfrz on 2009-04-23
i have wireless turned on. there is a button for it and it's on. i tried turning it on and off. it won't let me connect to a wireless router. and my neighbors(wireless) have been the same since i moved here so i'm not sure why they would changes channels. i don't know how to troubleshoot this. it was working just fine, i turned my computer off and the next morning i turned it on and it wouldn't connect :\ thanks for your input

---

### Post by nikonfrz on 2009-04-26
bump. still unsolved. i can't connect to any wireless connection. i don't know how it became unassociated because it wasn't before. any suggestions?

---

### Post by nikonfrz on 2009-04-26
kernel log
```
Apr 26 22:05:30 vpkeebs-laptop kernel: [ 3243.153663] ieee80211_crypt: registered algorithm 'WEP'
Apr 26 22:06:08 vpkeebs-laptop kernel: [ 3281.476054] ipw2200: Failed to send WEP_KEY: Command timed out.
Apr 26 22:06:09 vpkeebs-laptop kernel: [ 3282.484054] ipw2200: Failed to send SSID: Command timed out.
```

sys log
```
Apr 26 22:04:31 vpkeebs-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
Apr 26 22:04:31 vpkeebs-laptop NetworkManager: <WARN>  nm_device_wifi_set_enabled(): not in expected unavailable state! 
Apr 26 22:04:31 vpkeebs-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Apr 26 22:04:31 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto dlink' 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto dlink' has security, but secrets are required. 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Apr 26 22:05:25 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 26 22:05:26 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 1 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto dlink' has security, and secrets exist.  No new secrets needed. 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Config: added 'ssid' value 'dlink' 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'SHARED' 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 26 22:05:29 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 1 -> 2 
Apr 26 22:05:30 vpkeebs-laptop kernel: [ 3243.153663] ieee80211_crypt: registered algorithm 'WEP'
Apr 26 22:05:30 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Apr 26 22:05:31 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Apr 26 22:05:35 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 3 
Apr 26 22:05:37 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Apr 26 22:05:39 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 3 
Apr 26 22:05:40 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Apr 26 22:05:44 vpkeebs-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 3 
Apr 26 22:05:46 vpkeebs-laptop NetworkManager: <info>  eth1: link timed out. 
```

---

### Post by t0mppa on 2009-04-27
Sorry, that's way over my head there. Google finds quite a few posts with equal trouble, but no one seems to have found a proper fix for it. Looks like [some folks]("http://209.85.129.132/search?q=cache:AQJ2SFX_840J:ubuntuforums.org/archive/index.php/t-282.html+eth1+unassociated&cd=1&hl=en&ct=clnk&gl=fi&client=firefox-a") managed to set it up manually, but even that required entering the same commands every time they booted, so not a very good fix.

---

### Post by nikonfrz on 2009-05-12
Well i solved the problem. it was my room mates piece of **** router dlink. linksys has taken over lol

---

