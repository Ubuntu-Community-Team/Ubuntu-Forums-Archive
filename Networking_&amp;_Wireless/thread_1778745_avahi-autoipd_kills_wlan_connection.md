---
title: "avahi-autoipd kills wlan connection"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by barbar on 2011-06-09
I use kubuntu Natty and having issues with network-manager-kde I establish a wireless connection with /etc/init.d/networking. 
I can establish a network connection with this script. 
It is also executed during startup an a ip address is assigned to wlan0. But short after this it seems that avahi-autoipd is called and the already established connection is killed.

I am not sure if I need the avahi-autoipd (or avahi-daemon) and how I can prevent the avahi-autoipd script to kill an established connection?

---

