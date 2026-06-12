---
title: "Internet sharing hosts/networking"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by jasonbrfc1 on 2012-06-30
Hi there!

Looking for some advice for my system.

I currently have an Ubuntu pc with 2x network interfaces: eth0, wlan0

wlan0 connects the pc to my router/internet and eth0 is used to share the connection to another device (internet sharing through network manager)

My problem is that my routers ip range is 10.20.10.0/24 and eth0 is sending out dhcp on 10.42.43.0/24, ideally I need to be able to see the device thats connected to eth0 from the rest of my network.

from that device I can see my whole network but from the network back in I can't!

Is there something I need to set on the Ubuntu pc to get this working?

Thanks in advance

---

### Post by spiky001 on 2012-07-01
Hi  Have a look here [http://wiki.debian.org/BridgeNetworkConnections](http://wiki.debian.org/BridgeNetworkConnections)

---

