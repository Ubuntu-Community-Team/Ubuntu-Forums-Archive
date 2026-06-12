---
title: "network connects (via nm-applet) but does not work after using wpa_supplicant"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2013-03-26
Hey guys.

I had to use wpa_supplicant to connect my laptop to the WPA2 enterprise security at work.  I saved my old /etc/network/interfaces file to /etc/network/interfaces.bak before doing this.  Now I've restored the old file.  But my home network no longer works, even though it sees networks and claims to connect.

I believe I have restored all the old settings.  Really, the only change I made was to the /etc/network/interfaces file.  I did also create an /etc/wpa_supplicant.conf file, but I quickly deleted it after it failed to do what I wanted.  I restored the old /etc/network/interfaces file from the backup I made.

When I boot, the nm-applet comes up just like it should, and it claims to connect to my personal wireless network at home.  But it does not DO anything, i.e. I cannot browse the internet or download repositories, etc.

I can connect to my wireless network (and use it!) just fine with other wireless PCs at home.  So it's not that the network is down---it works just fine.  But the laptop I used to connect at work now fails to connect at home.

Any help would be much appreciated.  Thanks!

---

