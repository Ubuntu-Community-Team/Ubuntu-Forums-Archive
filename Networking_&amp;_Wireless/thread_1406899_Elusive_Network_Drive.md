---
title: "Elusive Network Drive"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by K-Sub on 2010-02-14
I recently bought a Dell Mini 10v running Ubuntu 8.04.  This is my first plunge into the world of Linux.  On my home network I have a network hard drive.  Sometimes when I log on to the Mini it can see the network drive, as well as the other computers on the network, sometimes it doesn't see anything on the network.  When it does see the network drive, sometimes it can access the subfolders, sometime it can't.  I have done a lot of searching on the forums and have not been able to find anything about intermittent connections.  Here is another wrinkle that may or may not be relevant, I also have a networked HP Laserjet printer.  Regardless of whether or not the Mini can see the network drive and the other computers, it seems to always be able to see and use the printer.  Any suggestions/ideas/tips?  Thanx.

---

### Post by K-Sub on 2010-02-14
OK, I managed to fix my problem.  In the file browser (Nautilus?) I went to Go - Location and then typed in smb://192.168.1.XXX, i.e. the IP address for the drive.  Once I got there, I set up a bookmark and I was done.  Now, whenever I want to go to this drive, all I need to do is click on the bookmark.  This worked so well that I also used it to log on to the disk drives on my Windows PC.  Worked there too.  I'm not sure why I was having trouble logging on to these drives before, but this works like a champ.

---

