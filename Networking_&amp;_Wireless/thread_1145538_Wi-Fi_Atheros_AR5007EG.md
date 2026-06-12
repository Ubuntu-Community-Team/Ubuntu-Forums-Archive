---
title: "Wi-Fi Atheros AR5007EG"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by k.nenad on 2009-05-01
I have instal Ubuntu 8.10 on Amilo Pi2540 with Wi-Fi card Atheros AR5007EG and i have a probles but i find [COLOR=Black]resolve[/COLOR].
This is the way:

System -> Administration -> Hardware Drivers
         if Support for Atheros 802.11 wireless LAN card is Green (activated) ok,
         if is not Green then click Activate.

Next step is:
System -> Preferences -> Network Connection
          click Wireless

Then open Terminal and write
           $ ifconfig -a

wlan0     Link encap:Ethernet  HWaddr 00:16:55:6f:e4:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:f0200000-f0210000 

copy the mac address (in this case is 00:16:55:6f:e4:7a) end go in Network Connections

click ADD in Wireless.
Connection name: wlan0
SSID: <something> (i write "N")
Mac Address: <paste mac-address>
MTU: 1500 or automatic

then click OK

I hope is helpful

And i'm sorry for my Bad English :)

---

