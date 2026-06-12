---
title: "Help with a simple configuration to connect a pc and router"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by Garret88 on 2011-12-13
Since I want to access to my openwrt router at my network's home I discovered I am forced to use OpenVPN. In fact the ISP which provides the internet connection doesn't allow his customers to be visible from the exterior (it is an Italian ISP named Fastweb). 

The pc with what I want to access my router from the exterior is connected to the internet with a public IP and I can open the doors I want. For this reason I want to install the openvpn server on that pc.

What I would like to achieve is to see all the devices connected on the openwrt router (and the router itself) from the PC with the public IP. 

For example, access the router web interface by simply writing 192.168.1.1 on the pc with openvpn server of which the local address is 10.0.0.2. 

At the same time I would avoid to install the openvpn client on each device connected to the openwrt router. Is this possible? So reach the 192.168.1.3 pc from my openvpn server pc with 10.0.0.2 as local address, without installing openvpn client on the 192.168.1.3 pc.

Is this kind of operation called "bridging"? I am pretty new with openvpn, so I came here to gently ask if you can suggest me some configurations for the openvpn server and client.

What would happen if I restart the pc with the openvpn server? I mean does the router with openvpn client automatically reconnect as soon the openvpn server is again on?

I think an image is better descriptive of what I want to build:
[img]http://i.minus.com/i16Aa1z94jN2I.png[/img]

Really thanks in advance.

---

### Post by philinux on 2011-12-13
Moved to Networking forum.

---

