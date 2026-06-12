---
title: "BT Home Hub Wireless Problems"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by monsi08 on 2010-09-18
Hi all,

I currently have a desktop PC (running 10.04) connected to the home hub (v2) via ethernet and everything works correctly. I want to change to wireless so I can move the home hub, I've tried several usb wireless adapters and always end up with the same issue. I can associate with the home hub it will hand out an ip address, answer dns queries and allow me to connect to its web setup page but not the internet (ping, web, etc). I also have a htpc (also 10.04) which is able to connect through the wireless correctly plus a laptop running XP.

Any help would be greatly appreciated, please let me know if more info is needed.


Desktop - Ubuntu 10.04 (gnome)
HTPC - Mythtv 10.04 
Laptop - Windows XP

Wireless Dlink G132, Belkin f5d7050, edimax EW-7711UTn (currently in use)
(Configured using wpa_supplicant)

BT Home Hub V2 (Black)

---

### Post by MCL34NS on 2010-09-18
i think i may be having the same problem as you and i cant see what the problem is. not sure if it is possible to fix or not.

---

### Post by grahammechanical on 2010-09-18
So that others are able to help you better than I can, would you please confirm:

1) The BT home hub is connecting to the ISP? what do the indicators lights reveal?

2) The desktop gets internet access when it is connected to the home hub by ethernet cable?

3) When you left click the network manager icon you see a list of available wireless networks? Is your BT home hub among them? My wireless is detecting a BTHomehub2, a BTFON, and a BTOpenzone network. The last two are unsecured. As well as other wireless networks. So, I know my wireless card is working. What do you see when you left click the network manager icon? This (I think is a easy way to tell if the network card is detected by the OS and activated.

regards.

---

### Post by monsi08 on 2010-09-18
Hi,

Just to confirm

1) The Home Hub is connected (power, broadband  and Wireless lights on), looking on its setup pages it has got an ip address and dns servers.

2) The desktop is currently connected by ethernet and works correctly, and other devices use the wireless successfully.

3) Network manager stopped working correctly (the icon is no longer shown on the top panel) somewhere along the line I don't know why, I have removed it and scanned for networks using iwlist scan which showed the Home Hub.  This is configured using wpa_supplicant with the same config file I use on the htpc which works ok.

Thanks

---

### Post by monsi08 on 2010-10-06
Hi, 

just to let everyone know I switched to using Wicd and apart from a few drop outs when it complains about an incorrect password its been working fine for over a week now.

---

