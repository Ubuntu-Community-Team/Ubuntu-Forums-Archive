---
title: "network mangement disabled - solved"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by mrmjb on 2010-10-30
Yesterday all of the linux boxes I'm involved with (3) expereinced the same problem simultaneously.

Network management was disabled and there was no graphical option to turn it on it affected KDE and Gnome desktops.

The solution was to edit /var/lib/NetworkManager/NetworkManager.state and turn all options to true.

To do this you will need to edit it as root so go to a comand line and use *sudo gedit  /var/lib/NetworkManager/NetworkManager.state* (or *sudo kate  /var/lib/NetworkManager/NetworkManager.state on KDE*) this should open your text editor with the corupted file.  It should say

[I][main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

[/I]The problem was the first line read *NetworkingEnabled=false *after deleting false and putting true you can either restart or issue *sudo service network-manager restart *and everything should be working again.

---

