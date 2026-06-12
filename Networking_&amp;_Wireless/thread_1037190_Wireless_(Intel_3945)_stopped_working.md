---
title: "Wireless (Intel 3945) stopped working"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by hurricane35 on 2009-01-11
SSIA. Just stopped working after last update to my ubuntu 8.10 laptop. The wireless toggle is turned on. I am wondering if it has something to do with my bluetooth mouse? Any help is very much appreciated. 

dmesg yields:
[92380.984105] wlan0: authentication with AP 00:1b:11:e4:ba:63 timed out
[92391.986980] wlan0: authenticate with AP 00:1b:11:e4:ba:63
[92391.990043] wlan0: authenticate with AP 00:1b:11:e4:ba:63
[92392.188215] wlan0: authenticate with AP 00:1b:11:e4:ba:63
[92392.389284] wlan0: authenticate with AP 00:1b:11:e4:ba:63
[92392.589106] wlan0: authentication with AP 00:1b:11:e4:ba:63 timed out
[92403.577336] wlan0: authenticate with AP 00:1b:11:e4:ba:63
[92403.776147] wlan0: authenticate with AP 00:1b:11:e4:ba:63
[92403.976126] wlan0: authenticate with AP 00:1b:11:e4:ba:63
[92404.176099] wlan0: authentication with AP 00:1b:11:e4:ba:63 timed out

wpa_supplicant.log yields:
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1b:11:e4:ba:63 (SSID='typhoon' freq=2412 MHz)
Authentication with 00:1b:11:e4:ba:63 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1b:11:e4:ba:63 (SSID='typhoon' freq=2412 MHz)
Authentication with 00:1b:11:e4:ba:63 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1b:11:e4:ba:63 (SSID='typhoon' freq=2412 MHz)
Authentication with 00:1b:11:e4:ba:63 timed out.

iwconfig yields:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by hurricane35 on 2009-01-15
bump!!!!!

Really need some help here! I am going crazy with this issue.

Thanks!!

---

