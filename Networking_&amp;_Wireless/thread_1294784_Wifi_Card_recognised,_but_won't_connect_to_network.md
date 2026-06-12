---
title: "Wifi Card recognised, but won't connect to network"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by TheWonkits on 2009-10-18
I have the Netgear WG111T, and I followed the guide on how to get it installed, and it worked.

But now, whenever I try connecting to my wireless network (WPA security enabled), the little symbol just goes around in circles for 5 minutes, then asks me for my key again. I know the key is correct, because I've been using this card in XP for a while and it works fine.
Someone told me that my key might be too many characters, it's 16 characters, for the record.

Here's exactly what I did:
Followed the instructions here
[https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)

Logged into Ubuntu, went to Wireless networks, entered "3NEKO08" as my SSID, then selected WPA personal as my encryption, and entered my 16 character password, and hit apply. It detects the network (sometimes) and will show me my signal strength (which is about 56%), and then sits there and tries to connect, but just keeps asking for my Key.

Did I do something wrong here?

---

### Post by smithy1155 on 2009-11-21
> **TheWonkits said:**
> I have the Netgear WG111T, and I followed the guide on how to get it installed, and it worked.
 
But now, whenever I try connecting to my wireless network (WPA security enabled), the little symbol just goes around in circles for 5 minutes, then asks me for my key again. I know the key is correct, because I've been using this card in XP for a while and it works fine.
Someone told me that my key might be too many characters, it's 16 characters, for the record.
 
Here's exactly what I did:
Followed the instructions here
[https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)
 
Logged into Ubuntu, went to Wireless networks, entered "3NEKO08" as my SSID, then selected WPA personal as my encryption, and entered my 16 character password, and hit apply. It detects the network (sometimes) and will show me my signal strength (which is about 56%), and then sits there and tries to connect, but just keeps asking for my Key.
 
Did I do something wrong here?
 
hey mate, i'm kinda having the same problem, however tonight i've just disabled my WPA key, and it managed to connect to the wireless router.

---

### Post by Master_Ne0 on 2009-11-27
Same problem, looks like a bug.

Waiting for more information (see below). Try open for now.

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/459716]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716")

---

