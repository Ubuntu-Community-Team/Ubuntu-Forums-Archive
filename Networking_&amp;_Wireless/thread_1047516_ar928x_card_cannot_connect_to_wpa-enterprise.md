---
title: "ar928x card cannot connect to wpa-enterprise"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by robere.it on 2009-01-22
Hello. I've bought a new laptop, and slapped Ubuntu Intrepid on it. The ath9k driver worked perfectly out of the box for unencrypted, WEP and WPA encrypted networks. However, I am unable to join to the encrypted network at my university. Whenever I try to use nm-applet, both "green circles" fill in, and then it hangs on requesting a network address. So, I disabled nm-applet and NetworkManager, and tried with wpa_supplicant and dhclient. Again, no go. wpa_supplicant correctly joins the network, but dhclient is unable to request a dhcp address. It DHREQUESTS a number of times, and then returns "no offers recieved". My wireless card is an Atheros ar928x.

Any insights?

---

