---
title: "Dell 1440 Networking Issue"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2009-09-08
Good morning everyone. I have recently inherited a new Dell 1440, and have been running into all kinds of quirks and problems. My old E1505 worked great, but it is no longer with us in this world. :(

The Dell 14 has a mini half card in it. The Ubuntu wireless manager connects fine to WEP, WPA, etc. However, when I try to do a few things in the command line, or use Kismet, I get the following issue:

> 
iwconfig

lo        no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:243  Noise level:166
          Rx invalid nwid:0  invalid crypt:8  invalid misc:0


eth2 can be connected to a access point, streaming data, working just fine, but iwconfig shows nothing... any thoughts on this? I'm fine if Kismet won't work with the card, but I figure this might be one of the problems? Why doesn't eth2 show anything, even when she's connected up? When I try to use iwlist with eth2, it says it doesn't support scanning (But the network manager can scan around just fine). Any help which you can provide would be great. Thank you. :)

---

