---
title: "Avoid sending hostname via dhclient using NetworkManager"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by alberto666 on 2012-01-08
I have been trying to modify the dhclient.conf file to avoid sending hostname via dhclient.

However, when I use NetworkManager rather than dhclient command line utility, it instead uses this file:
/run/nm-dhclient-wlan0.conf (if wlan0 interface is used)

And..., the problem is that it adds this line:
send host-name "XXXXXXXXXXXXXX"; # added by NetworkManager

Where XXXXXXXXXXXXXX is my real hostname.

The point is that I don't want my real hostname to be sent, but rather no hostname or a hostname I define, but it seems impossible, since NetworkManager removes any "send host-name" line and adds its own with the real hostname.

However, if instead of using NetworkManager I use dhclient, everything works perfectly. 

Any idea on how to use NetworkManager and don't send the hostname defined in the computer?

(FTR: the reason I don't want to send it is because I travel a lot, use public WiFi's and I don't want my real hostname (which includes my real name) to sent, neither to use static IP configuration, I'd like a solution using my dhclient.conf files and NetworkManager, but avoid NM from modifying my conf. files).

Thank you very much,
Alberto.

---

