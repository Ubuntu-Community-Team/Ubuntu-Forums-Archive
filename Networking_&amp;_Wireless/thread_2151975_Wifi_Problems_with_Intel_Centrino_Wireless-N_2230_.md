---
title: "Wifi Problems with Intel Centrino Wireless-N 2230 on Ubuntu 12.04"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by labboy0276 on 2013-06-06
Hi,


So I have searched high and low and nothing seems to work.  I bought this Lenovo p500 IdeaPad, got rid of Windows8 and threw Ubuntu 12.04 on here.


My Centrino Wireless-N 2230 card seems to be giving me trouble.  It will be at full speed at times (25MB down / 5.5 MB up) then drop to almost nothing (~2MB down / `0.5MB up) for no reason what so ever.  Usually within 5 minutes of rebooting.


I have tried everything out there on the web.  I have disabled Wireless N, I have turned off Power Management, I have disabled ipv6, etc etc.  Most changes seem to work initially and then not at all.  So is there a solution someone may have or help in the matter.  It has been a couple years since I have used Linux, so any help with commands and trouble shooting would be greatly appreciated.


Here are some terminal stuff:


rfkill list

[HTML]
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[/HTML]

iwconfig

[HTML]
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"Birchcrest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:744:0A:FA   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:130  Invalid misc:203   Missed beacon:0
[/HTML]

---

