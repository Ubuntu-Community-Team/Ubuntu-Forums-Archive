---
title: "Routing incoming packets to other ethernet device"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by wimpelmeesje on 2009-09-14
I'm trying to get connection to Xbox Live on my Xbox 360 by connecting it to my laptop with an ethernet cable. The laptop has internet via wifi.

I've managed to share the internet by setting the "Share with other computers" on my eth0 (cable to the Xbox) in the network manager. When I test the connection on the Xbox it has access to the internet and Xbox Live but the NAT-setting is moderate and I would like this to be open.

To discover where the problem occurred (either the laptop or the router blocking some port) I sniffed the packages on both devices with Wireshark while running the connection test on my Xbox. It revealed that there were four packets that my laptop did receive, but that didn't get sent to my Xbox, which (I think) should have happened.

This is the (UDP) package:
Source: Xbox Live Server, port 3300 (mcs-calypsoicf)
Destination: 10.0.1.4 (my laptop), port 3074 (xbox)

The other packages that my laptop does send to the Xbox are all on port (source and destination) 3074 and the communication is initiated by the Xbox. The package descibed above isn't. My guess is that there isn't a NAT entry on my laptop which causes the routing software to think the package is for my laptop.


To solve this, I would like to tell the routing software to route all incoming packages on my wireless device (eth1) with destination port 3074 to my Xbox (which is on eth0).

I've searched a bit on Google and these forums but haven't found an answer yet. Probably because I don't know the correct technical terms :).

---

### Post by Iowan on 2009-09-14
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for Internet/Connection sharing. Near the end is a link for sharing via [wireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless").

---

