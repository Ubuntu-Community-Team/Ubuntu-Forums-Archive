---
title: "WLAN connection goes on/off and is slow after update in 9.10 and is still th in 10.04"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by jar112 on 2010-05-06
So wireless problem in laptop Thinkpad T41 (Intel PRO/Wireless LAN  2100 3B Mini PCI Adapter). My problems already began in 9.10 after some  recent update. The wireless connection went really slow (had been  working fine in 9.04 and 9.10 until ~ two weeks ago) and started to  loose connection every other minute. Especially if downloading  something. And this happens even 2 m from the router. Wired connection  is ok.

iwconfig gives:

eth1    IEEE 802.11b  ESSID:"Hoblaa"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point:  00:0C:F6:66:E6:8C
          Bit Rate=5.5 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:362  Invalid misc:55   Missed beacon:12

I've got nothing... Anyone?

---

### Post by jar112 on 2010-05-06
> **jar112 said:**
> So wireless problem in laptop Thinkpad T41 (Intel PRO/Wireless LAN  2100 3B Mini PCI Adapter). My problems already began in 9.10 after some  recent update. The wireless connection went really slow (had been  working fine in 9.04 and 9.10 until ~ two weeks ago) and started to  loose connection every other minute. Especially if downloading  something. And this happens even 2 m from the router. Wired connection  is ok.

iwconfig gives:

eth1    IEEE 802.11b  ESSID:"Hoblaa"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point:  00:0C:F6:66:E6:8C
          Bit Rate=5.5 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:362  Invalid misc:55   Missed beacon:12

I've got nothing... Anyone?

Hmmm... setting the router to "B" (11 MB/s) and changing the channel seems to make it work. At least it's not disconnecting anymore. Speed is not quite the same as 54 MB/s but still it works.

---

### Post by Tamalin on 2010-05-06
This problem is sounding eerily familiar, I have had the exact same thing.  What is the output of nm-tool?

---

