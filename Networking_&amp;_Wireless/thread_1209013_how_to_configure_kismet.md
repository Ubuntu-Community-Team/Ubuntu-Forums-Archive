---
title: "how to configure kismet"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by ramazani on 2009-07-09
hi guys i been looking on the internet and the fourm did not find any match to sort out my problem can anyone tell me how to run kismet on ubuntu 9.04 here is my deatail card down below 


kanishixan@kanishixan-laptop:~$ sudo airmon-ng start wlan0
[sudo] password for kanishixan:                           


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
2722    NetworkManager
2742    avahi-daemon  
2743    avahi-daemon  
2747    wpa_supplicant
3429    dhclient      
Process with PID 3429 (dhclient) is running on interface ra0


Interface       Chipset         Driver

ra0             Ralink 2560 PCI rt2500
wlan0           Atheros         ath9k - [phy0]
                                (monitor mode enabled on mon0)

kanishixan@kanishixan-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.                                                
Enabling channel splitting.                                              
FATAL: Unknown capture source type 'mon0' in source 'mon0,wlan0,ath9k'   
Done.                                                                    
kanishixan@kanishixan-laptop:~$ clear                                    


kanishixan@kanishixan-laptop:~$ sudo airmon-ng


Interface       Chipset         Driver

ra0             Ralink 2560 PCI rt2500
wlan0           Atheros         ath9k - [phy0]
mon0            Atheros         ath9k - [phy0]

kanishixan@kanishixan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"apsecuritynorth"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:0F:B5:18:E8:F4
          Bit Rate=24 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-78 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mon0      IEEE 802.11abgn  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kanishixan@kanishixan-laptop:~$

---

