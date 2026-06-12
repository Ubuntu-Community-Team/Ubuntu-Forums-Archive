---
title: "Network Manager/nm-applet Problems"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by End3r on 2008-12-10
Using Intrepid
network-manager version 0.7~~svn20081018t105859-0ubuntu1.8.10.1
network-manager-gnome version 0.7~~svn20081020t000444-0ubuntu1.8.10.1

After a recent update (though it has probably been a month or so now; I'm not sure which update it was) I noticed that trying to connect to a network by clicking the network icon in the panel and selecting a network caused nm-applet to seg fault and disappear. This wasn't a big issue because I remained connected to my wired network and didn't need the wireless for anything.

I recently tried to fix the issue by reinstalling network-manager and network-manager-gnome, but unfortunately this has only made the issue worse:
Now network manager won't connect to my wired connection on boot, and I'm forced to use "sudo dhclient eth0" to connect.

I have tried reverting to older (i.e. those available on packages.ubuntu.com) packages of network-manager/network-manager-gnome and that did not help.

Any help would be greatly appreciated!

Let me know if there is any other information I can supply.

---

