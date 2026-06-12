---
title: "Athk5 - Wireshark does not capture trafic even in Promisc mode (AR2425 &gt; AR5007EG)"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by skuro on 2009-06-24
[Solved] : It was a simple problem... It was in promiscuous mode, the problem was that i enable WPA in my router. And i didn't know i had to add the Key to Wireshark. ( But a doubt now is... How to add a wpa key in a libpcap c code? )

Hi guys, 

Im using Jaunty, i used to sniff my own wireless network with a random madwifi driver, but now that i went to the latest Athk5 it isnt working!

Im not in a switched network, its wireless traffic, and im in the network. it had to be easy do capture it. 

I can put my card in Promiscuous mode with no problem, but it isn't capturing any traffic besides the one destined to me. What to do? (my card is an Atheros AR5007EG > AR2425 )

> 
wlan0     Link encap:Ethernet  HWaddr 88:a7:38:52:5a:48  
          inet addr:192.168.1.101  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::8aa7:38ff:fe52:5a48/64 Scope:Link
          UP BROADCAST RUNNING [COLOR="Sienna"]**PROMISC**[/COLOR] MULTICAST  MTU:1500  Metric:1
          RX packets:9657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6864547 (6.8 MB)  TX bytes:1873515 (1.8 MB)


p.s: I tried to remove, unload and uninstall athk5 and go with Madwifi again, but it didn't work. Im not managing to go back to the state were i used to sniff with no problems... And now i want a solution, it doesnt make sense. Why i cant capture traffic in Promiscuous mode?

Skuro, Thanks in advance.

---

