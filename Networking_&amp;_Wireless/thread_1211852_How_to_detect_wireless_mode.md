---
title: "How to detect wireless mode"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by itsjareds on 2009-07-13
I was looking around on the Internet for wireless cards that are compatible with Linux and Windows. I found [this one card]("http://www.amazon.com/AirLink-AWLL3028-802-11g-Wireless-Adapter/dp/B0017GS382/ref=sr_1_1?ie=UTF8&s=electronics&qid=1247470418&sr=8-1") that seems perfect, with a low price and it's listed on [Ubuntu's compatibility list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion").

The only problem is that it says:

> - IEEE 802.11g: 6/9/12/18/24/36/48/54 Mbps (auto-sensing) Access Method: Infrastructure mode
- Ad-hoc mode (802.11b Ad-hoc)

I'm not sure which access mode my network is, how do I check it? Also, does the above quote mean that this card can connect to both types of connection?

Thanks.

---

### Post by Silverdagger on 2009-07-13
im not sure if im 100% correct but i believe that just means that card is capable of those modes... you can change a Wireless cards mode in the terminal by typing: sudo iwconfig <interface> mode ( from their you can choose manged, monitor, ad-hoc... etc. )

---

### Post by itsjareds on 2009-07-13
Alright, thanks.

---

### Post by Silverdagger on 2009-07-13
No problem, hope i was able to help some...

---

