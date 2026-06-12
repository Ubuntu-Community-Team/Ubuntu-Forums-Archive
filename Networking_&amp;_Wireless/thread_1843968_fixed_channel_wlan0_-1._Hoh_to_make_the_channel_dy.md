---
title: "fixed channel wlan0: -1. Hoh to make the channel dynamic"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by rootnet47 on 2011-09-14
Well I'm new to Linux and I'm using Oneiric Ocelot Alpha 3 . I'm just trying to crack my own wireless connection using aircrack-ng.
here I'm trying to run following command 

# airmon-ng

Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
mon0        Intel 4965/5xxx    iwlagn - [phy0]

# airmon-ng start wlan0 6

Found 2 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
901    NetworkManager
902    avahi-daemon
903    avahi-daemon
1271    dhclient
3588    wpa_supplicant
Process with PID 5826 (sudo) is running on interface wlan0
Process with PID 5827 (airodump-ng) is running on interface wlan0
Process with PID 8717 (airodump-ng) is running on interface wlan0

Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
                (monitor mode enabled on mon5)
mon0        Intel 4965/5xxx    iwlagn - [phy0]
mon1        Intel 4965/5xxx    iwlagn - [phy0]

#airodump-ng -c 6 --bssid 00:24:B2:7E:2E:94 -w psk wlan0

once I hit enter, I got

 CH  6 ][ Elapsed: 0 s ][ 2011-09-14 19:11 ][ [COLOR=Red]fixed channel wlan0: -1[/COLOR]          
                                                                               
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH E
                                                                               
 00:24:B2:7E:2E:94  -54 100       36      627  175   6  54e  WPA  TKIP   PSK  N
                                                                               
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes     
                                                                               
 00:24:B2:7E:2E:94  00:1C:BF:7F:11:C1  -61   54e-54e    45      627

and where I found [COLOR=Red]fixed channel wlan0: -1[/COLOR].
 
and after that I tried to make four way handshake by command 

aireplay-ng -0 1 -a 00:24:B2:7E:2E:94 -c 00:1C:BF:7F:11:C1 wlan0

but 

[COLOR=Red]# aireplay-ng -0 1 -a 00:24:B2:7E:2E:94 -c 00:1C:BF:7F:11:C1 wlan0
19:35:09  Waiting for beacon frame (BSSID: 00:24:B2:7E:2E:94) on channel -1
19:35:09  wlan0 is on channel -1, but the AP uses channel 6[/COLOR]

which is not sound good. Where

#iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  Mode:Monitor  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon0      IEEE 802.11bgn  Mode:Monitor  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


One more thing I should notify that whenever I tried to connect to my wireless network I've failed . I think this may be happnd because of the channel.  Could anyone help me to solve the problem?

---

### Post by Dangertux on 2011-09-14
There are 3 possibilities here.

1 -- Your wireless drivers are not properly patched to support injection.

2 -- You need to end the processes listed in airmon-ng and try again

3 -- You're staying connected to your wireless and actually trying to inject into another network.

Eitherway you should try the aircrack-ng forums. This isn't something that is really supported here.

---

### Post by uRock on 2011-09-14
Please seek help with network cracking tools elsewhere. It is not supported here.

---

