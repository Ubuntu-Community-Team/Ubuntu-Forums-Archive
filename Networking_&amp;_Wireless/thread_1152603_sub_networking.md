---
title: "sub networking"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by drummerstiggs on 2009-05-08
Here's the situation, I'm new to Linux so I'm not sure of any settings. I have a home network set up with XP machines and a wireless router.  I have a laptop currently in my room running xp that can access the internet wirelessly.  I now have a dual boot ubuntu/xp tower that I want to use also.  The tower does not have a wirelss card.  My main objectives are to use the tower as a file server for the laptop only.  I would like to be able to connect using a cat5 cable between the laptop and tower for both file sharing and if possible to piggy back off the wireless of the laptop to access the internet on the tower for updates, etc.  any help would be great.
 
Thanks

---

### Post by milton1 on 2009-05-08
You should be able to create an ad-hoc network by plugging the tower into the laptop, then enabling the "share this network connection" option on the wireless connection on the laptop will allow the tower to use the laptop as a proxy. I don't recall the full details of setting up the ad-hoc network, but a brief google search should find them easily enough. One detail I do know, however, is that you will need a crossover cable for the computer-to-computer connection. A normal cat5 patch cable will not work.

---

### Post by Iowan on 2009-05-08
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for Internet/Connection Sharing (ICS) Toward teh end is a link for [wireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless").

---

