---
title: "One cure for being repeatedly asked for passphrase"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2013-01-23
Executive summary:  If you're having N speed connection problems with  being repeatedly asked for a pass phrase and have your own router,  perhaps consider dd-wrt or another 3rd party firmware.  


I've had an wireless router connection problem/solution I thought I'd mention.  I see on the networking and wireless forum people getting frustrated by repeatedly being requested to enter a WiFi pass phrase but never getting a connection.  I came by an inexpensive used Linksys WRT-300N wireless router.  It is an early draft-N  or Pre N device from around 2006.  I brought it home, did a hard reset, entered the appropriate info, set WPA2 personal and the aformentioned problem reared its head.  I could connect at G speeds but if I selected 'N' speed only, no go. I'd be repeatedly prompted for the network pass phrase but no connection.  If I tried compatibility mode it would always connect at G speeds, never more than 54 Mb./sec. These adapters would connect to another router - ActionTec MI424WR - but that device is limited to 65 Mb./sec and compatibility mode seemed slow.  I knew however that the adapters would connect at speeds > 54 Mb./sec using WPA2 encryption.  There hasn't been a new firmware released for the Linksys WRT300N since 2006 or 2007 and even that is no longer available on Cisco/Linksys site.  

What REALLY annoyed me is that it would connection in Windows 7 but not in Ubuntu/Xubuntu/Mint.  Huh?

I knew about dd-wrt but hadn't had the courage to risk bricking a router.  Here was a good reason to give it a go, the device was of limited use in its present state.  I carefully read the instructions, downloaded the appropriate file, held my breath and pressed "install". The install completed without incident, I power cycled and hey, lookit there!  I can now connect *buntu machines with N speed adapters at N speeds.  Now to learn about wireless bridge mode and other new-to-me goodies. :D   I'm sure this solution  will not fix every occurrence of this problem but it worked for me.

---

### Post by ahallubuntu on 2013-01-23
Yeah, DD-WRT is awesome.  (Tomato too if it works on your hardware.)  What's cool about DD-WRT is that it adds a lot of cool features to your router that consumer routers rarely have.  For example, the larger image of DD-WRT (only fits in routers that have enough NVRAM and RAM) has a built-in OpenVPN server.  So you can set that up and connect into your home network and wake up any servers you want to access via WOL to get to files or whatever.  (Wake-On LAN is also built into DD-WRT.)

---

