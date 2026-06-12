---
title: "I need to set up a wireless network"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by realboy236 on 2009-12-10
I have ubuntu ultimate edition 2.3 installed on my sister's laptop and I have windows vista installed on my laptop, and I want to know how to share files through a wireless connection with her. the only thing is that we don't have a router or internet connection at our house, so will it be possible to do it? thanks if you can help.

---

### Post by gordintoronto on 2009-12-10
The easy answer is to get a wireless router.  Prices start around $20.  It doesn't have to be connected to the Internet to work.

There are other ways to share files: a USB flash drive, or "null modem" ethernet cable to plug into both computers.  A 2 GB flash drive should cost less than $10, a cable might be less than $5.

---

### Post by Iowan on 2009-12-10
It should be possible.  I'll see if I can find a How-To for Ad-Hoc networks.

[Here]("https://help.ubuntu.com/community/WifiDocs/Adhoc") is one - hope it helps.
[Another]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting") that may be useful.

---

### Post by FuManShu on 2009-12-10
NetworkManager can handle ad-hoc networks.  Just click on the network logo on the top right, go to create new wireless network, type a SSID and voila! go to the Windows laptop and connect to it.   If you're having issues, right-click the network logo --> Edit Connections --> Wireless then click the network and make sure the infrastructure says ad-hoc.

---

