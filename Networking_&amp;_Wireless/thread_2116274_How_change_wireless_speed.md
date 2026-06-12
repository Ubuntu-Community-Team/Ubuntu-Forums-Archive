---
title: "How change wireless speed ?"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by kapetr on 2013-02-15
If I run:  

**iwconfig wlan0 rate 2M**

after some time I get i confirmed by **iwconfig wlan0**. 

But in fact - nothing is changed. I can see in wireshark (radiotap header) 11Mbit/s and the real speed is unchanged - in my case >5Mbit (limited by my ADSL link to ISP). So - how can I really change speed of WiFi link ?


++ change: now I see in Radiotap Header 2Mbit at outgoing frames, but 11Mbit by incoming frames are unchanged (dowload speed >5Mbit). 

Any Ideas ? It is possible at all to force - lowering speed of link 
client <-> AP ? In both directions ? 

Thanks.

P.S.: I it is possible - it is settable in NM ?

---

