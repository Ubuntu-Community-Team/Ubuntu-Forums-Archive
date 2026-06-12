---
title: "Endless wireless password request"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by Yitzach on 2013-01-17
I have a poor wifi spot in this house, distance being the issue. After it drops, if I don't get on the wireless password request and get the computer reconnected in a certain amount of time, Linux queries the empty room again, and again. I assume I'd end up with something like this, but I didn't think to check it: [http://imgur.com/3egL8](http://imgur.com/3egL8). Is there any way to get the thing not to ask me every 5 minutes if I don't get back to it? It's not like asking the room at large repeatedly is going to help when I'm not here.

OS: Ubuntu 12.04.1
WiFi card: Broadcom 43xx
Supported by firmware-b43-installer and not the proprietary driver

iwconfig:
wlan0:
IEEE 802.11bg  ESSID:Network Name  
Mode:Managed  Frequency:2.412 GHz  Access Point: 68:7F:74:21:7B:CD   
Bit Rate=54 Mb/s   Tx-Power=20 dBm   
Retry  long limit:7   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality=37/70  Signal level=-73 dBm  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:66  Invalid misc:101   Missed beacon:0

---

