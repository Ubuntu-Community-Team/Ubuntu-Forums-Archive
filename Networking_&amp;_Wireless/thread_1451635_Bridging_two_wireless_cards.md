---
title: "Bridging two wireless cards?"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by sucramreverse on 2010-04-10
I've been at this for a couple days now to no avail, so I figured I'd ask here. I want to have two wireless cards in one machine bridge an internet connection. One will connect to the internet (wlan0) and the other will act as an access point (wlan1).

I admit this may seem like an odd thing to do, but my reasoning is that the LAN with internet access has WPA and my Nintendo DS does not support WPA. I have no control over this network, as it is what I set up for my neighbor but he insists on having WPA security. Therefore I'd like to have this computer connect to the WPA network and then bridge that to an open/WEP access point.

There seems to be plenty of guides for setting up a bridge from ethernet  to wireless and vice versa, but trying to go off these guides for  bridging two wireless cards has gotten me nowhere.

I got the two cards installed, with drivers (one native and one  ndiswrapper), and could see them in ifconfig and iwconfig. They could both  connect to the network/internet individually, so they were working fine. However the first block came in that it would not let me set one of them to Master mode.

(Also, how can I set everything back to where I started, without reinstalling ubuntu? I now have to remove the second card or ubuntu freezes on startup...)

---

### Post by 2hot6ft2 on 2010-04-10
Sounds like ICS to me just substitute one of the wifi cards for eth0 in the instructions.
[Internet Connection Sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

---

