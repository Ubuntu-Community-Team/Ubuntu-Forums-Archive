---
title: "Mythtv broken after update (mysql?) - fixed!"
date: 2009-11-14
forum: Mythbuntu
---

### Post by GeekPapa on 2009-11-14
Hi.

I am running Mythbuntu 9.04 amd64 on an intel 9400 over biostar/nvidia motherboard with 4 gb ram and 2.6TB disk.  I have a Hauppauge PVR-250 pci tuner and it's been running great until I did an update recently (two weeks ago).  Now, the mythbackend doesn't find the card (complaining about "No UPnP Backends Found") when I run mythtv-setup.  It is getting a 111 error trying to connect to mysql and I noticed that the mysqld is not running.  

I can watch TV with VLC and mplayer.  All the ivtv tools work great, but no point in running mythbuntu if you're not going to use it.  This is why I have GbE in my house!

So I started mysql with /etc/init.d/mysql start and then ran myth-setup.  It upgraded the mysql schema and mythtv-setup worked correctly after that.  Whew!

---

