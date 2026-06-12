---
title: "No wireless or wifi 10.10 following upgraded router"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by SnoopFogg on 2010-12-14
Upgraded broadband service yesterday and now using a combined router and modem (Virgin Media Hub).  But I now have no wired or wifi internet connectivity on either of my ubuntu 10.10 systems.  I tested it on my work laptop which uses Window and it works fine for wired and wifi.

With 10.10 I no longer have a network icon upper right panel to check, so not sure how to set up wireless. Both machines have static IP addresses and are able to ping each other but there is no internet connection on either.  

Please let me know if there's any info I can post to help diagnose the problem. Any help appreciated.  Thanks

---

### Post by SnoopFogg on 2010-12-16
Anyone know why a wired internet connection might work on Windows but not Ubuntu?

---

### Post by grahammechanical on 2010-12-16
First, go to System>Preferences>Startup Applications and look for network manager in the list and see if there is a tick mark against it. If there is not, then click on the network manager line to make network manager activate at startup. Reboot. You should now see a network manager icon.

Second, did any instructions come with the router/modem. You will need that information to set up connections in network manager, especially if you want to connect to the router/modem by wireless.

Regards.

---

### Post by SnoopFogg on 2010-12-16
Hi, thanks for the response.  Checked the network manager and it is ticked in the startup apps list.  Then tried manually running the command "nm-applet --sm-disable" in a terminal which gave an error message saying "An instance of nm-applet is already running".  There's no icon though and so I can't see how to get the list of available networks.

On the wired connection front, I checked the manual (which of course only shows windows and mac) but basically says just plug it in and it should work.  I've never had to amend anything in the past on Ubuntu to get a wired connection to work.  It always just worked.

At the moment I'll settle for anything just to get a connection as I can't do anything without one.  Any more thoughts?  Cheers

---

### Post by SnoopFogg on 2010-12-16
Ok, I've got a wireless connection now via System>Preferences>Networkconnection.  It's pretty slow though - slower than it was before and it is supposed to be twice as fast now, but I now have a network icon which is great.  

On the network icon the wired network is all greyed out, but at least I can see and connect to the wireless networks. Maybe just need help doing a similar manual addition for a wired connection?  I tried Add Wired Connection. On the wired tab I've put in the device mac address - by this I mean the mac address of the router. I've left the cloned mac address blank - does that need to be completed?  If so, with what?  MTU I've left as automatic - does this need to be changed?  And I haven't done anything with the other three tabs (802.1x Security, IPv4 Settings, IPv6 Settings).  Should I do anything with these?

Further update:  tried following some other advice to:
Edit /etc/NetworkManager/nm-system-settings.conf and set managed=true where you see:

[ifupdown]
managed=false

While on the wired network i can now see (not greyed out) Ifupdown (eth0). But it still is not connecting to the internet.  I think that the people having the greyed out problem for wired network were still able connect, just resolved the greyed out problem.  I'm going to revert back to: managed=false

Thanks

---

### Post by SnoopFogg on 2010-12-16
All sorted.  Changed back from static ip address and now working.

---

