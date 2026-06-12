---
title: "Ubuntu detects my wireless card, but doesn't connect"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by mmmpancakes on 2006-06-17
I finally for the networking panel to detect my wireless card Linksys WPC54g.

I have an open access point (broadcast ssid, no wep key). My other computers can easily log onto the network, but my ubuntu laptop won't. It detects the SSID, but just won't connect.

Thanks in advance for any help!

---

### Post by x64Jimbo on 2006-06-17
try sudo dhclient <interface>

---

### Post by mmmpancakes on 2006-06-17
And how do I know what my interface is?

---

### Post by mmmpancakes on 2006-06-17
This is what comes up. Seems a little strange.


Listening on LPF/wlan0/00:12:17:3e:7b:f6
Sending on   LPF/wlan0/00:12:17:3e:7b:f6
Listening on LPF/eth0/00:e0:b8:53:cd:f7
Sending on   LPF/eth0/00:e0:b8:53:cd:f7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14

---

### Post by Tobbz on 2006-06-17
Are you using any kind of encryptions (WEP/WPA) on your wireless network?

Which brand and model is your wireless card?

---

