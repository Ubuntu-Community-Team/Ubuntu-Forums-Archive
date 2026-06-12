---
title: "BackTrack 4 AAO wireless issues"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by SchindlerShadow on 2010-10-09
I know, I know, this isn't about Ubuntu really, but BT4 is based off Ubuntu now so here i go, :P 

i have an aao AOA150 (i think 150 lol, the tag is faded XD) 

i followed this guide: 
[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

i followed that tut (link is up their^) and at iwlist wlan0 scan it says no results, even though their is 5 open connections around me. i connected to my ssid anyway from the next step and it looks like it works, no errors, but running ifconfig after running dhclient wlan0, still shows no ip, dhclient wlan0 gave me an error no DHCPOFFERS received, then No working leases in presistent database - sleeping. :confused:

and I even tryed: (from BT4 fourms)

/etc/init.d/networking start 

/etc/init.d/NetworkManager

/etc/init.d/wicd

and wicd still shows no networks can be found. i tryed putting it to madwifi via options in wicd, still no. :(

i used to use ubuntu :P and i know my way around the CL, but i never connect to a wifi via cl :lolflag:

am i missing something? :confused: can some one help a noob? thx alot :P

---

