---
title: "Kismet configuration,need help"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by liglio on 2010-10-30
[B]For 2 days i`m hardly trying to configure kismet,but unsuccessfully...now I`ll tell you more about it
I use ASUS k50 ab notebook,it has wireless device but I use another usb one which is also ASUS wireless adapter...so when i IWCONFIG i get this : 
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"BTC-ADSL"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1E:73:50:38:13   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My english is not very good,maybe this is the reason to be not able to configure the source line in the conf file....will somebody explain me exactly what to write in the source line please ? 


root@pearl:~# kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan1): Enabling monitor mode for madwifi_ag source interface wlan0 channel 6...
ERROR:  Unable to create VAP: Operation not supported
ERROR:  Unable to create monitor-mode VAP
WARNING: wlan0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
Done.
root@pearl:~# 








[/B]

---

