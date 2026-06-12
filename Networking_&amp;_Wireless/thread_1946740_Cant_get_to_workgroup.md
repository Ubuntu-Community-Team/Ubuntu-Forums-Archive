---
title: "Cant get to workgroup"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by smuggly on 2012-03-25
I have a new install of ubuntu 11.0 64 bit. I setup my smb.conf file. My problem is strange. i can see my windows home network,but can only get as far as WORKGROUP. when i click on workgroup i get the Dbus error cant access? Any help would be appreciated. I can transfer files from my win 7 box to ubuntu no problem. Please advise. Thanks 
Hers som info.


I Got It With This Post From
[http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)
	

jldupont:

I've had very good results in mixed network environments (window-ubuntu) with this method:

1) Press alt+F2 >> type gksu gedit /etc/nsswitch.conf

2) Look for this line: hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

3) Add "wins" so it looks like this: hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

4) Install the "winbind" package: sudo apt-get install winbind (or via software center or synaptic)

5) Reboot or restart your network



Thanks...Smuggly

---

