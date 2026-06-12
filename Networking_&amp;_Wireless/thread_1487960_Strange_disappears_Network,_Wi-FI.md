---
title: "Strange disappears Network, Wi-FI"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by Blur4eg on 2010-05-19
Good evening everyone! 
I beg you to help with a problem: 
There are 12 computers in the office. I've decided to completely convert to Ubuntu 10.04. He told people to thrive, all beautifully described ... 
Translated for 5 machines of different configurations. Small flocks of frequent visitors: That share drives after rebooting the printer is not seen networked PC (cured by adding ```
sudo service smbd restart
``` at the end of [B]/etc/init.d/cups/[B]), 
a herds Samba climbs. A day like all ustakanilos: Samba picks network, network printers without problems printing. 
BUT! All, without exception, the machines periodically (one every 1-2 hours) vanishes wi-fi, in such a way that the Network Manager says that the connection is there. Ie connect to an AP saved, but neither network nor Inet is not working. 
At 3 typewriters Wi-Fi adapter Asus WL-167G (chip Ralink 2571), in 2 - Dlink DWA-125 (the same chip, Ralink 2571). 
Can be treated with all the simple reconnection to the Wi-Fi network, and again for an hour or two. 
Read about shitty Ubuntovskogo Network Manager `a. Exit - install Wicd. No sooner said than done: 
```
sudo apt-get remove network-manager-gnome 
sudo apt-get remove network-manager 
sudo apt-get install wicd 
```
Configured, but .... The problem remained! With the same frequency falls off Inet, Wicd says that the connection to the access point is. Reconnection - works. 
As access points are used routers Linksys WR54, DHCP disabled, encryption, WPA2. Points is 3, all work on the same channel. 

The team, help me not to fall face in the dirt in front of employees) 
Another option - set all through wpa_supplicant, but I doubt it will work or not.

---

