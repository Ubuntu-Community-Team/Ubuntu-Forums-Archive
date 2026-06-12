---
title: "[SOLVED] eth1 becomes eth2 after a reboot"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by RavenOfOdin on 2006-06-08
What the heck is going on? 

I recently rebooted my system (after a KDM hangup while installing a new theme, and on restart of Xserver) then once I got back in to Network Settings, I find that eth1 (the slot once taken up by my wireless card, and now by another NIC) has become eth2.  This has screwed up my Firestarter settings as well as my head. . .Lol.

Could anything be causing this?
I've saved the new hardware profile just in case.

---

### Post by mindwarp on 2006-06-09
As long as this doesn't happen again, what prohibits you from configuring firestarter for the new interface name?

---

### Post by RavenOfOdin on 2006-06-09
[QUOTE=mindwarp]As long as this doesn't happen again, what prohibits you from configuring firestarter for the new interface name?[/QUOTE]

Nothing, but its m*****f***ing annoying.

---

### Post by RavenOfOdin on 2006-06-09
And BTW, I don't want to go through that each and every time it changes.

---

### Post by mindwarp on 2006-06-09
You can open up your firestarter rules in gedit, do a search / replace all and have it done in short order.  Now I have had my interfaces change names once, directly after an install, and then it never happened again and I filed a bug for the installer.  If this is happening more frequenty, you probably would be best served to visit [www.launchpad.net](www.launchpad.net) and filing a bug report

---

