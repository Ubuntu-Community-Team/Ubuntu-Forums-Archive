---
title: "OpenVPN Subnet Problems"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Tim H on 2010-02-16
Hi all,

I'n pretty new at this stuff and am having trouble setting up openvpn. I Currently have a Windoze homeserver for my files, I want to load Ubuntu Server on it and have remote access to it using OpenVPN. I dont want to open up my entire network to the VPN so I am tring to set up a Tun device with no bridging.

I am trying to make this work first on my Ubuntu Desktop before I replace the Server's operating system as it does work right now although access sucks. I can get OpenVPN to establis a connection to the desktop from my work laptop, but for some reason the desktop and the laptop are on different subnets. the Sever application sets itself to IP 10.8.0.1 on subnet 255.255.255.0 when the client connects, it is assigned and IP of 10.8.0.6 on subnet 255.255.255.252. 

This has me baffled, and I can find no help on forcing the client on the laptop to the same subnet.

Thanks

---

