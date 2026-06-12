---
title: "radius gateway"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by realburb on 2011-08-05
Hi, I use my ubuntu box with eth0 and  wpa_supplicant to connect to a wired radius controlled LAN, I can update get internet connection, can see every other PC in the network and so forth.

I also installed a asus pce-n13 which supports ap mode and with hostapd, I was able to set a draft-n  AP up.

Which means I got eth0, lo, and wlan0. 

I have a lot of clients which are not able to use 802.1x authentification, but can connect to the WLAN I set up with the pce-n13. 

There is a radius server and a dhcp server on the LAN at eth0. 

I would like every machine connected to my ubuntu box via wlan0 to get its IP from the dhcp server of the eth0 attached LAN, but let the ubuntu box handle the 802.1x authentication, as one of the clients is a plain TV, which doesnt understand radius.

I have eth0 br0 and wlan0. but  I got no idea, how to allow client authentication or even working bridging.

Please help me, I will add any  needed information.

---

