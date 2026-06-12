---
title: "Can't get printer shared"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by conedude13 on 2006-04-25
I don't think I need some bloated program that can do the 2 little things that I want and then a ton of other things.  All I want is to share my printer from my ubuntu breezy badger box to my wifes xp laptop, and to get an ftp server up and running for the misc shared files that I would like to share between the two.

I have tried the basic printer sharing tutorial, but was not able to connect to my ubuntu box from the xp laptop.  Both are on the same LAN through a lynksys router.  Any help would be greatly appreciated, thanks!

---

### Post by Jose Catre-Vandis on 2006-04-25
The wiki printer sharing tut worked for me, with an HP Deskjet 720C. The important bit was typing in exactly the correct name for the printer, in all places, otherwise sharing didn't happen. Also, if you are using Dapper, check your cups files as it has been updated twice and maybe this has been overwritten. Oh, I see you are on Breezy, but perhaps the same has occured?

For an ftp server, search ftp server in Synaptic, The only Ubuntu marked ftp server appears to be **vsftp**, but there are others: **wu-ftpd**, **pure-ftpd**

If you want to do something with a web interface, install apache and php and use a script like "Andromeda" for mp3s (streaming) and "Snif" for files

---

