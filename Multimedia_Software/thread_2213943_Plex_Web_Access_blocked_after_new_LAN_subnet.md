---
title: "Plex Web Access blocked after new LAN subnet"
date: 2014-03-29
forum: Multimedia Software
---

### Post by TheFu on 2014-03-29
Had to re-IP my LAN today so VPN access would be easier.  Completely switched subnets - from 192.168.x.x to 172.22.x.x.

Now I'm working through all the things that were broken by this across the physical and virtual systems here.

So - Plex Media Server seems to be impacted by the change, but I can't figure out how to tell it about the new subnet.

BubbleUPnP from android works fine.  Can't see any issues. Both devices (tablet, phone) are on the same new subnet as the server.

PleXBMC does not work. It won't connect to the plex server RUNNING ON THE SAME PC!!!

Plex web interface redirects to myPlex login. It never did this before. I believe it thinks my browser is trying to access from outside the LAN, so it is trying to protect the content like I'm coming in over the internet. I do not nor do I ever plan to have a myPlex login. This is 100% LAN access.

Searching through the millions of files under /var/lib/plex* didn't show any settings - 
**/var/lib/plexmediaserver/Library/Application Support/Plex Media Server** is where the base starts for any files.

Now SOLVED - as usual, trying to describe this issue helped me find the solution.  There is a file, **Preferences.xml**, at the top of that deep directory structure. Inside are 3 places with the 192.168.x.x networking - changed each to be 172.22.x.x as needed, restarted the server and the website is working again.
BTW, the default plex website is : [http://IP:32400/web/](http://IP:32400/web/)

PleXBMC plugin is working too.

---

