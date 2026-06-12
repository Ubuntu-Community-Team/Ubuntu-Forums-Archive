---
title: "aireplay authentication fails"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by mihamil on 2009-02-26
I am attempting to learn to crack wep on my wireless router.  The router is running dd-wrt.  Everything is default except that wep is enabled.  Mac filtering is off. the router is on channel 6 and sits about 4 feet from the computer I am attempting this with.

I am using ubuntu 8.04 and a WPC11 V3 PCMCIA card.

I have blacklisted the orinoco drivers, so the hostap driver are successfully loading and the computer is operating with them.

I am successful at putting the card in monitor mode, using airodump-ng to get the bssid and station mac addresses (The station mac address is of a laptop sitting right next to me as well).  I then set up a command to send the authentication and a command to start arpreplay and inject packets.

The authentication keeps failing.  It just says "Sending authentication request" over and over.  I have checked everything in the message at the bottom regarding reasons it may be failing and I think I'm doing everything right.  Obviously I'm not otherwise it would be working.

I have scoured the web, forums, etc for 2 weeks trying to figure this out but am still unsuccessful.  I have loaded the patched firmware on the card successfully.  I don't know what to do??? :confused:

These are the commands I'm following 
*************************************************
airmon-ng start [interface]

airodump-ng -w capture -c [channel]

aireplay-ng -1 0 -a [BSSID of the network] -h [Connected clients MAC address] -e [ESSID or Network Name] [Interface]

aireplay-ng --arpreplay -b [BSSID of the network] -h [Connected clients MAC address] [Interface] 

airodump-ng -c [Channel] --bssid [BSSID of the network] -w [Capture file name] [interface]

aircrack-ng -z {This starts the PTW attack which is much faster} [Capture file name]
***********************************************

The card has the prism chipset which aircracks says is compatible but I can't get it working.

I have also tried Backtrack 3 LiveCD and gotten identical results.

Any ideas?

---

### Post by mihamil on 2009-03-04
Anybody have any ideas.  I tried also using a WPC54G card and the first time I attempted this is sent an authentication request.  Returned as successful once but then failed association. After that it acted just like the WPC11 card before.  Just attempts authentication over and over.

---

