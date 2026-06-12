---
title: "Network Manager and WEP 128bit"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by AtticusHashmal on 2011-03-24
I'm having issues connecting to a WEP 128 bit protected network when I use Network Manager.
 
Basically, I can connect to WEP 64bit & WPA protected networks just fine through Network Manager, and I'm able to connect to WEP 128 bit networks by setting the key manually through iwconfig, but then when trying to reconnect later on with Network Manager it will not connect.
 
One thing I've noticed is that when attempting to connect with Network Manager, iwconfig shows 'Security mode: open' after the encryption key, but if I set the key manually in iwconfig, once I get the 'Connection Established' message popup iwconfig then shows 'Security mode: restricted'. I can't see any option for this in Network Manager except possible Open/Shared Key but changing to Shared Key seems to cause it to fail quicker than with Open so I'm guessing that's not it.
 
Any ideas? Thanks.
 
Ubuntu 10.10 btw.

---

