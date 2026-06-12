---
title: "Won't connect to open (unsecured) WiFi networks"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by ViewFromTheBoundary on 2010-07-09
Hi,
I have no problem with my wireless network at home, or visiting friends, but it won't connect to public, open, unsecured WiFi networks, eg hotels, trains, ships.
I'm using Ubuntu v9.10, NetworkManager applet v0.7.996, on a Dell Inspiron 1750 laptop.

If I left click on the NetworkManager, the available wireless networks are displayed and I can see the relevent open networks, named as expected and shown without the lock icon.  I click on the relevent entry, watch a spinner for 30 seconds or so and then it drops off and I have no connection.  This happens for "all" open connections.

If I look at my defined Wireless Network Connections now, I can see, eg, "Auto Internet@Sea,  Last used: never".  Editing that connection:

[Wireless]
SSID: Internet@Sea
Mode: Infrastructure
BSSID: (blank)
MAC address: (blank)
MTU: automatic

[Wireless Security]
Security: None

[IPv4 Settings]
Method: Automatic DHCP

[IPv6 Settings]
Method: Ignore

I've run out of things to stab at blindly.  Can anyone help in an informed way??

---

### Post by nerdy_kid on 2011-03-11
I have this problem too.  It happens with my STA driver and with r8187l.  My laptop has a BCM4312 802.11b/g LP-PHY (rev 01) card in it.  Switching to the b43 driver allows me to connect to open networks with my laptop card (not the other chip that uses the r8187l driver).  dhclient cant get an IP, which is where connecting fails. Anyone have any ideas?

---

### Post by wilshere on 2011-03-28
I have exact same problem. I am able to connect to wi-fi at home which is WEP secured.
I am unable to connect at office which is public wi-fi. Am able to connect to it thru windows.

---

