---
title: "Wireless Internet sharing (win xp host ubuntu 10.04)"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by AdmiralNotorious on 2010-05-05
Ok guys, i've got some problems.

 -I have an imac 2008 
 -a windows partition on the imac (xp professional)with wireless adapter
 -a dell Inspiron 1501 laptop with Ubuntu 10.04

i want to make a wireless internet sharing network between my desktop windows partition and my ubuntu laptop. I have already gotten it working between Mac os x and ubuntu, but in windows there is no internet. I wish to remedy this with your assistance. 

-and please, don't recommend that i buy a router, i'm broke

---

### Post by Iowan on 2010-05-05
There are a couple of ICS help pages, [this]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") one covers wireless.

---

### Post by AdmiralNotorious on 2010-05-05
That turtorial is for an   -UBUNTU HOST TO A WINDOWS CLIENT-


i want a -WINDOWS HOST TO AN UBUNTU CLIENT-


i know im in an awkward position asking for mostly windows advise here at ubuntu forums; but these forums are so much more organized, reliable and gratifying than the windows ones, and there is a lot of ubuntu to this question too.

---

### Post by egor604 on 2010-05-06
This configuration seems to work for me:

VPN connection shared to wifi connection.

Vista Server:
ssid: example
auth: WEP Shared Key

ip: 192.168.0.1
mask: 255.255.255.0

Ubuntu client:
ssid: example
mode: adhoc
key: WEP(40,128 bit key) Shared 


Same configuration works well with:
Vista(XP, 7) <-> Vista(ICS server)
Nokia N810 (linux tablet) <-> Vista(ICS server)

---

### Post by AdmiralNotorious on 2010-05-07
can anybody post a true guide with clear steps? The more detailed and specific, the more i will appreciate

---

