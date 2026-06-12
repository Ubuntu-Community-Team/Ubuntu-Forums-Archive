---
title: "setting up wireless network"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by frog3764 on 2009-05-25
I have a pc (Windows XP)on a modem, a second pc wireless with XP.  I just upgraded the wireless caqed to a DLINK DWA 510 so it would be compatible with Ubuntu.  My router is a DLINK Gamer Lounge DGL 4300 and this has worked well with XP.  Now the Ubuntu docs scare me on trying to set up this lan for Ubuntu.  Is there a easy and simple way for this Newbie/dummy to get this set up, as I don't understand most of the docs concerning this?  I really don't want to go back to Windows!  All help is appreciated.

Thanks, 
Jim

If I can get this set up, then I will upgrade from my Edgy 6? to the new version 9.04.

---

### Post by Henrike Corinna on 2009-05-25
Hi,

             First of all, verify that each of your devices are connected to the accesspoint, and that they can ping each other.
(the thinkpad can ping the desktop for  instance). 
Then, install a private proxy (like privoxy) on the thinkpad. Remember the privoxy port, probably 80 or 8080.
While the thinkpad is connected to the internet, on the desktop configure the IE6 settings to use a proxy, whose IP address is your thinkpad address and the port being 80 or 8080 like privoxy settings.
And that's all, everything works.

---

