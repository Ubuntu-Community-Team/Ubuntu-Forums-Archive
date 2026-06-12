---
title: "Aireplay-ng. No ARP requests or packets sent"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by species-001 on 2011-08-17
Hi, been googling and searching for a solution to this problem I am having.

Briefly I can't get an ARP request from my wifi network and I am sending 0 packets.

here is the following info, could anyone recommend a solution ?

sudo airmon-ng start wlan0 6

Interface    Chipset        Driver
wlan0        Atheros     ath9k - [phy0]
                (monitor mode enabled on mon0)

sudo airmon-ng -c 6 mon0

 CH  6 ][ Elapsed: 2 mins ][ 2011-08-17 18:48                                         
                                                                                                
 BSSID   PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID             
                                                                                                
 00:24:D2:0A:BF:56  -51 100     1198      191    0   6  54   WPA2 CCMP   PSK  battle cruiser (my network)

sudo aireplay-ng -3 -e "battle cruiser reporting" mon0
No source MAC (-h) specified. Using the device MAC (D8:5D:4C:D1:1C:27)

18:51:18  Waiting for beacon frame (ESSID: battle cruiser reporting) on channel 6
Found BSSID "00:24:D2:0A:BF:56" to given ESSID "battle cruiser reporting".
**Notice: got a deauth/disassoc packet. Is the source MAC associated ?** 
Read 34241 packets (got 0 ARP requests and 619 ACKs), sent 0 packets...(0 pps)

sudo airplay-ng -0 0 -e "battle cruiser reporting" mon0 

gives this

19:03:19  Sending Authentication Request (Open System) [ACK]
19:03:20  Authentication successful
19:03:20  Sending Association Request [ACK]
19:03:20  Association successful :-) (AID: 1)

---

### Post by realzippy on 2011-08-17
So log in another machine in your network,then you will get an arp request.
Btw,
this forum is not the right place to discuss such software.
Tons off stuff are out in the net about aircrack ng.
If you cannot solve your problem with that information,you should learn a few network basics first.

---

