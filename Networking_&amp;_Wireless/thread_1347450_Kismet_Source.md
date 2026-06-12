---
title: "Kismet Source"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Dhaann on 2009-12-06
Hello, I've installed Kismet on my PC and I'm trying to configure it. In the kismet.conf file I put my username, but the problem is the source. I currently have this: "source=madwifi_ag,wlan0,wlan0" but when I run kismet I get this output:
> 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for madwifi_ag source interface wlan0 channel 6...
ERROR:  Unable to create VAP: Operation not supported
ERROR:  Unable to create monitor-mode VAP
WARNING: wlan0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
Done.
I also did "iwconfig wlan0 mode monitor" and tried to start kismet again, but that didn work.. Also, madwifi_g and madwifi_b doesn't work too. Maybe this will help (output of iwconfig wlan0):

> wlan0     IEEE 802.11bg  ESSID:"8242AA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:92:BD:C3:FA   
          Bit Rate=36 Mb/s   Tx-Power=3 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:C2B4-45E0-F4A0-7D73-5B75-1BD1-F74A-A231 [2]
          Power Management:on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Anyone who knows something about this?

---

