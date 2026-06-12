---
title: "Medion Akoya and wifi NM &amp; WICD :'("
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by zenacim on 2009-05-31
hi everyone,


i have a medion akoya (ralink chipset) and installed ubuntu 9.04

i used ndiswrapper first and Network Manager.

The NM could see my wifi network on WPA2 but impossible to connect.
i tried some tricks saw on the ubuntu forums but none worked.

i tried to compile the drivers, i think it's ok.

Now i installed WICD the ethernet works fine but no wireless connection is available:'(

what can i do please

> 
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



> 
iwlist ra0 scanning
ra0       No scan results



thank u for ur support

---

### Post by zenacim on 2009-05-31
i changed my interface file and now i can see all wifi network


my network is on WPA2-auto / TKIP / PSK encryption

i cannot connect.

someone can help me please??

---

