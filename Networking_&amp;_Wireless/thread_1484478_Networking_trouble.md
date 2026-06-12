---
title: "Networking trouble"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Unclewilly_76 on 2010-05-15
When I try to connect to my network  my netbook connects but then send my router a Deathentecation signal and dissconnects, theis happens both on my wireless and ethernet!   
I think this problem began awhile ago when I tried to plug in my cellular usb dongle..
 
Any ideas

---

### Post by Iowan on 2010-05-16
I don't have a netbook, so I'm not sure what all is different...
Have you checked the Network Manager settings to see if anything has changed there? I doubt anything has changed in */etc/network/interfaces*, but you can see if it still has only the two lines defining "lo".

---

### Post by Unclewilly_76 on 2010-05-18
The netbook remix has a different GUI and may be slimmed/optimized down a little but aside from that I don't think there is much difference.   I'm pretty new to Ubuntu and looking in the network manager shows my interfaces, lo,Ath0,wlan0 as well as other information but I don't have much clue what I could change to make my connection stay connected.
 
When I try to connect wirelessly or wired the computer actually does connect (so says the routers log) but then sends a deauthentication packet (so says the routers log) and then disconnects.   What's even stranger is that when I enable monitor mode on my wireless card using airmon-ng I can then scan for networks, etc, etc...   
 
Is there some way I can do a system restore or something?   
 
It's strange and I thought maybe my router banned my netbook because I was attacking my network using the netbook ...  That's why I chacked the routers log and seen that it actually does connect briefly and then disconnects - same on both interfaces, ath0 and wlan0...
 
I may just reinstall the OS and start from scratch because I'm dual booting beside XP and it's become quirky on start-up, on top of this other issue...

---

