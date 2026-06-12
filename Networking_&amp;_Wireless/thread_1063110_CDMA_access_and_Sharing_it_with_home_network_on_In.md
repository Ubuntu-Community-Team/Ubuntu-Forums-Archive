---
title: "CDMA access and Sharing it with home network on Intrepid"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by photonian on 2009-02-07
*I connect to the Internet using CDMA (Verizon Mobile Service)*and want to share my internet connenction via eth0 (local home network).
Everytime I have an Internet connection through CDMA (ppp0) then plug the network cable in (eth0), the system (Ubuntu Intrepid) starts looking to eth0 for the Internet and ignores my ppp0 connection.
After this I no longer can get on the internet, because although ppp0 is still up the system will only look at eth0 for the Internet.

I can unplug the ethernet(eth0) then the system will turn back to my already online ppp0(CDMA) and give me access to the internet, but then of course I can't share my internet connection with my home network.

_[CENTER]**I *need to share my CDMA (ppp0) internet connection* with my Home Network (eth0)**[/CENTER]_

Please HELP!

P.S. 
     In Hardy I Used:
[LIST=1]
[*]Network Manager for eth0
[*]gnome-ppp for ppp0
[*]And Firestarter for DHCP and Sharing from ppp0 to eth0
[/LIST]

But _this doesn't work in Intrepid_, even when I got gnome-ppp to work for ppp0 (for which I had to make a group with ID 30 and include myself in the group)
:cry:

---

### Post by //yardo on 2009-03-25
Were you ever able to get this to work. I'm interested in the same type of setup.

I have a home network that I use to share files between computers but access the internet via CDMA device. When I connect to my home network that connection takes precedence over the CDMA connection and I'm not able to access the internet.

Any solutions to this are appreciated... Thanks.

---

### Post by inobe on 2009-03-25
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

wired

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

wireless

---

