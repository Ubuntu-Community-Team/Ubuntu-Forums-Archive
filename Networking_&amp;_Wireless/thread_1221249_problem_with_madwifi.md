---
title: "problem with madwifi"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by davewickett on 2009-07-23
**problem with madwifi **  				 ok i had a problem with my madwifi & ar424x card working with kismet , aircrack & other tools on ubuntu what i need is my Atheros ar5007eg to work with packet injection i think what i need is my madwifi to be patched this is what version of madwifi i have 

"svn co [https://svn.madwifi-project.org/madwifi/...l-0.10.5.6]("https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6")"

my wifi is working 100% but kismet is not 
1, how to apply patch to this driver (command)
2, or do i need to update my madwifi driver i think this driver does suport packet injection ive been trying to fix this for days now none stop i need on to my next step so some help would be so helpful 

and when i start my card in monitor mode it changes names to aswell now to like ath1 in sted of atho my card does go into monitor mode 

her is some info i hame trying to learn just need a bit of help 

davewickett@davewickett-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath1 IEEE 802.11g ESSID:"" Nickname:""
Mode:Monitor Frequency:2.457 GHz Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:16 dBm Sensitivity=1/1
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=45/70 Signal level=-51 dBm Noise level=-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ath0 IEEE 802.11g ESSID:"karenjohn" Nickname:""
Mode:Managed Frequency:2.412 GHz Access Point: 00:1E:2A:14:5A:46
Bit Rate:54 Mb/s Tx-Power:16 dBm Sensitivity=1/1
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=45/70 Signal level=-51 dBm Noise level=-96 dBm
Rx invalid nwid:7295 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

davewickett@davewickett-laptop:~$

i can kill ath1 when i try to start airmon-ng i get this

troot@davewickett-laptop:/home/davewickett# airmon-ng start wifi0 9


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID Name
3144 NetworkManager
3164 avahi-daemon
3166 wpa_supplicant
3167 avahi-daemon
5287 dhclient
Process with PID 5287 (dhclient) is running on interface ath0


Interface Chipset Driver

wifi0 Atheros madwifi-ngError for wireless request "Set Frequency" (8B04) :
SET failed on device ath2 ; No such device.
ath2: ERROR while getting interface flags: No such device

ath1 Atheros madwifi-ng VAP (parent: wifi0)
ath0 Atheros madwifi-ng VAP (parent: wifi0)
ath2_rename Atheros madwifi-ng VAP (parent: wifi0)


or
airmon-ng start ath0 9


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID Name
3144 NetworkManager
3164 avahi-daemon
3166 wpa_supplicant
3167 avahi-daemon
5287 dhclient
Process with PID 5287 (dhclient) is running on interface ath0


Interface Chipset Driver

wifi0 Atheros madwifi-ng
ath1 Atheros madwifi-ng VAP (parent: wifi0)
ath0 Atheros madwifi-ng VAP (parent: wifi0) (VAP cannot be put in monitor mode)
ath2_rename Atheros madwifi-ng VAP (parent: wifi0)
 
please fi there is some1 who could help me thanks 

dave :confused::confused::confused:

---

