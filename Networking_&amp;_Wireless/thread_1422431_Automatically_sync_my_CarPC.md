---
title: "Automatically sync my CarPC"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by aflores3 on 2010-03-05
I recently installed a PC in my car running [LinuxICE]("http://wiki.openice.org/index.php?title=LinuxICE"). In my home, I am running an Ubuntu Server.

The carPC has a 250 gig hdd. On the server, I have a dedicated partition of 250 gigs. What I want to do is have my car automatically sync with the server every time I enter my LAN via wifi. 

The idea is that I can legally copy my cds on the server, create a symlink to the /home/carpc/Music directory on the "carPC partition" of the server. Then, the next time my carPC is on within wireless range, it will automatically grab the new songs. It would also act as a backup if/when my carPC hdd dies. It would be nice to have some sort of notification on the carPC that it is currently syncing so that I don't turn it off in the middle of a sync.

The reason I put this in networking & wireless is b/c I could figure out a script to sync the two locations. What I dont know is how to have it start upon connecting to my home's wifi.

---

