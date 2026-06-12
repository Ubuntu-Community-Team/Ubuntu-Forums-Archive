---
title: "rtl8187 drivers. Not connecting from command line but connecting from NetworkManager"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by MastroLindo on 2009-02-19
Hi all. Sorry for the double post but the last one might lead to incorrect thoughts about the problem. I am quite sure that the problem is related to the drivers rtl8187 that my device is using.
From the networkmanager of gnome I have no problems in getting the connection working. (right now the access router is without any wireless security protocol enabled, but of course that it is just to test the connection).

From the command line I can (at least it seems so running iwconfig) get assigned to the correct AP using only the essid (iwconfig wlan0 essid TEST).

But after that DHCP request to get an IP adress timeout and even static IP config don't let me ping the router or anything on the network.

with iwlist wlan0 scan sometimes I see only the AP I am assigned, sometimes all the APs around... it appears to have a random behaviour..

Sorry again for the double post, if you want you can close the other one, since it's useless now... ([http://ubuntuforums.org/showthread.php?t=1073544](http://ubuntuforums.org/showthread.php?t=1073544) )

---

### Post by MastroLindo on 2009-02-19
I think drivers are not really the problem here.
Tried the same card with the same drivers and tools, on another machine (with fedora) (from the command line), it worked.

Tried 3 different cards on mine pc, didn't work. From gnome, they all work without any problem with the NetworkManager. So I just need to find out what it is making differently that I am not doing from the command line... 
no clue until now anyway..

---

### Post by MastroLindo on 2009-02-19
Found out why it was not working.

The answer was the gnome manager itself. Once uninstalled command line commands started to work again properly. 

I hope this helps if somebody has the same issue.

---

