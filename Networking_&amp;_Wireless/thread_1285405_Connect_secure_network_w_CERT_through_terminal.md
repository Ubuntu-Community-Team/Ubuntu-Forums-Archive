---
title: "Connect secure network w/ CERT through terminal"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by senorgomez on 2009-10-07
Hi,

I would like to know how to set up my ubuntu with no xserver device with my university network. 

At home, I can connect to my wireless network through the following config:

iface eth0 inet dhcp
wpa-essid ****
wpa-psk ***

 And that works fine. 

Now I want to connect to my university secure network, and the following guide is the only avaliable information. It is for wpa_supplicant however, not for /etc/network/interface:
(See Advanced Networking)

**[http://www.cs.umn.edu/help/network/wireless-linux-wpa.php](http://www.cs.umn.edu/help/network/wireless-linux-wpa.php)**

Can I convert that wpa_supplicant.conf information to the syntax in /etc/network/interfaces?

---

