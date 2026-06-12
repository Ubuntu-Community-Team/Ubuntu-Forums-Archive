---
title: "no network manager, cant connect wireless"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Capadac on 2009-04-27
im having a problem when i try to connect wireless in ubuntu studio 9.04, where is the network manager? i have a broadcom BCM4318 which works perfectly in ubuntu 9.04 but not the studio because i cant find network manager i did go to system>administration>network and then i unlock, but when i try to enable the wireless i have to do it manually and the weirdest thing no wpa, this is such a headache, oh yea i also download the broadcom firmware cutter or something like that

---

### Post by jerboyd on 2009-04-28
you will need to connect to the internet with a LAN cable and install network-manager-gnome with this command in the terminal
sudo apt-get install network-manager-gnome
then restart and you should see the nm-applet in the notification bar and you should be able to choose a network to connect to.

good luck

---

