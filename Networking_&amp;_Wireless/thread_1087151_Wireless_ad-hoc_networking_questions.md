---
title: "Wireless ad-hoc networking questions"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by slouchez on 2009-03-04
Everything ok in regular station mode - connected to an AP etc...

But I'm doing embedded wifi development in ad-hoc mode - and on my target I'm using the madwifi tools - of course an Atheros chipset  - and all the commands are there for config and management...

However such isn't the case on my laptop - a Dell n1525 where the logical device is wlan0 but there is no command that I can find that's the equivalent of 'wlanconfig' from madwifi - and iwconfig and iwpriv are incomplete.

The GUI utility wifi-radar does appear to allow setting ad-hoc mode but in fact it doesn't - as evidenced below:  

THIS IS WHEN I SET the wireless interface IN AD-HOC MODE using wifi-radar
===> MODE remains Managed
sylvain@sylvain-laptop:/dev$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"viiwrx"  Nickname:"viiwrx"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:4D:4A:72:A6   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=76/100  Signal level=-58 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


===> This is my normal setup
sylvain@sylvain-laptop:/dev$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"SLLFLL"  Nickname:"SLLFLL"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:4D:4A:72:A6   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=74/100  Signal level=-60 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sylvain@sylvain-laptop:/dev$ 

Questions: 
[1] what is available for ad-hoc networking on the Dell 1525????

[2] on my embedded target "iwconfig" also displays the key (WEP key) that was entered. so I know whether I have a key entered or not, and whether I am in "Open" or "Shared key" authentication mode. Here on the laptop there's no indication of any kind.
Where do I find the Dell wireless- specific utilities to address all this?

[3] networking in ad-hoc mode between 2 Dell laptops (Inspiron 1300 with XP and Inspiron 1515 with XP) ping works in one direction only. Note that my routes are setup correctly, and in fact I can FTP between laptops

[4] networking in ad-hoc mode between 2 Dell laptops (Inspiron 1300 with XP and Inspiron 1525 with Ubuntu) networking doesn't work at all. Note that my routes are setup correctly as well.

Questions 3 and 4 are there because that's what I see and may be someone else has an idea - but I can workaround. 
I am however "dead in the water" without a solution to [1] and [2]. 
Thanks in advance

---

