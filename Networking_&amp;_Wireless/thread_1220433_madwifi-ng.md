---
title: "madwifi-ng"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by davewickett on 2009-07-22
hi i have an atheros ar5007eg wifi card  ar424x  with madwifi-ng this is my madwif-ng driver .

"svn co https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6"

everything is fine i have wifi now but with my tools like aircrack and stuff it is not working i am new to all this but really want to learn ive been trying everything to fix this 
as you can see ath0 is been added by ath1 ath2 and so on 

davewickett@davewickett-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-51 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath0      IEEE 802.11g  ESSID:"karenjohn"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:2A:14:5A:46   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-51 dBm  Noise level=-96 dBm
          Rx invalid nwid:7295  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

davewickett@davewickett-laptop:~$ 

i can kill ath1 when i try to start airmon-ng i get  this 

troot@davewickett-laptop:/home/davewickett# airmon-ng start wifi0 9 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
3144    NetworkManager
3164    avahi-daemon
3166    wpa_supplicant
3167    avahi-daemon
5287    dhclient
Process with PID 5287 (dhclient) is running on interface ath0


Interface    Chipset        Driver

wifi0        Atheros        madwifi-ngError for wireless request "Set Frequency" (8B04) :
    SET failed on device ath2 ; No such device.
ath2: ERROR while getting interface flags: No such device

ath1        Atheros        madwifi-ng VAP (parent: wifi0)
ath0        Atheros        madwifi-ng VAP (parent: wifi0)
ath2_rename        Atheros        madwifi-ng VAP (parent: wifi0)


or
airmon-ng start ath0 9 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
3144    NetworkManager
3164    avahi-daemon
3166    wpa_supplicant
3167    avahi-daemon
5287    dhclient
Process with PID 5287 (dhclient) is running on interface ath0


Interface    Chipset        Driver

wifi0        Atheros        madwifi-ng
ath1        Atheros        madwifi-ng VAP (parent: wifi0)
ath0        Atheros        madwifi-ng VAP (parent: wifi0) (VAP cannot be put in monitor mode)
ath2_rename        Atheros        madwifi-ng VAP (parent: wifi0)


remember i am new go easy on me i really need to sort this out please if any1 could help me it would make me so happy i am getting stressed out now trying to do it all day and night  thanks

---

### Post by mashveloo on 2010-03-03
i have this problem

---

