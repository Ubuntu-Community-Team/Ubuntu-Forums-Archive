---
title: "KDE wireless network configuration (KWiFiManager?)"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by charles.figura on 2006-05-30
So I must be the dumbest wireless network user around.

I use several different wireless networks with my laptop.  For years I've been using some simple scripts to set the essid and key for each one.  That works well enough, no complaints, but I'm curious - is there an accepted KDE tool for handling multiple wireless networks?  It looks as if KWiFiManager is supposed to be able to do this, but I can't figure out how to configure it.  KWiFiManager docs suggest that use is trivial.  Docs my left... leg.  

If there's someone out there using KWiFiManager for this, please give me a little help.  Will it store WEP keys?  What's the format for entering them?  The standard tricks I use on iwconfig don't seem to work worth dip.  I don't even seem to be able to use it to connect to either my home or office networks (64 and 128 bit WEP).

And if there's something better, please clue me in.

Thanks.  My scripts aren't bad, but I like KDE, and I'd like to know what the KDE way is.

---

### Post by markr on 2006-05-31
I have been using knetwork manager sucessfully on my laptop,  it detects wireless networks in the area, allows me to connect to my own wireless network (WEP) and will also handle wired networks.

I recommend giving it a try,  search on this forum for knetwork manager for details of installation etc.

My WEP key is help in KWallet and KNetwork manager can access this when it connects to the network.  The only slightly annoying 'feature' is that kwallet starts every time you reboot and you are forced to enter you SU password.

Mark.

---

### Post by charles.figura on 2006-05-31
Thanks!  I installed KNetworkManager, and it's exactly what I was looking for!  Even easy to figure out.

---

