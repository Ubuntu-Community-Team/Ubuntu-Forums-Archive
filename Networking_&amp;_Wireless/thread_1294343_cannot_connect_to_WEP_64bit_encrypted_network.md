---
title: "cannot connect to WEP 64bit encrypted network"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by Cue2 on 2009-10-18
As the title suggests I'm having trouble connecting to my access point using 

Ubuntu 9.04 
2.6.28-15-generic i686

Medion Pentium M 1.7 centrino notebook
Intel PRO/Wireless 2200BG

in Network Manager when I try to connect to the router "DLRouter" and input my 64bit WEP key (using WEP 40/128bit)
the icon next to the time just spins for a very long time then it asks for the WEP key again. I know the key is right since it works on all other devices. I switched to wicd instead because I read somewhere that NM doesn't support 64bit WEP but wicd doesn't connect either. it seems to get stuck on "Authenticating" I then tried to switch the WPA_Supplicant driver from wext to ipw  but still no luck connecting. There is no mac address filtering on the router. The killswitch is on and I unplug my ethernet cable when I try to connect to it with wifi.

I don't know much about linux so please can you point out if anything here looks out of the ordinary. To me it seems fine except the channel:0 on the iwlist scan (due to auto channel scan on router). I spent the whole of Saturday looking for solutions trying to fix this but I have run out of ideas and I'm on the verge of giving up. So any suggestions would be greatly appreciated.

---

