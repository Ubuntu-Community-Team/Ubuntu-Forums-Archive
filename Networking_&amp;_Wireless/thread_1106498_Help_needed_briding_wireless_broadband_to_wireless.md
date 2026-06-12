---
title: "Help needed briding wireless broadband to wireless lan"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by TheHeathen on 2009-03-25
Hi there, have spent a lot of time trying to work out if this is possible or the best way to do it if it is... your suggestions would be appreciated. While there is lots of information about bridging wired/unwired networks, nothing seems applicable in this case.

I have a desktop connected to T-Mobile wireless broadband (huawei E220 usb dongle) configured through KNetworkManager. There is also an onboard wireless lan (rtl8187), configured (unmanaged) as master through /etc/network/interfaces (using the aircrack drivers). I would like to bridge these two connections to create a local wireless network accessing internet via the E220 with the desktop as an access point.

I am not sure if this is possible or if there is a better configuration to provide internet to the local wlan (other than getting a wired internet connection of course). 

The wireless broadband interface (ttyUSB0) does not show up in iwconfig, and PPP0, which is related somehow does not show up until the network manager loads. On the other hand, KNetworkManager does not seem to support master/AP connections for the local lan... mmmm stuck

I guess I need to configure both interfaces in /etc/network/interfaces to get the system working, but have no idea how to get the E220 working in this way. I did have the E220 set up in 7.04 using a dial up client, but don't really want to go back to this as the native support is so good now (8.10, 64 bit). Another alternative (preferred) would be a gui alternative to KNM  that can support both networks.

Any ideas or suggestions would be most welcome. 

Thanks, H

---

### Post by inobe on 2009-03-25
are you trying to share the internet ?

slimming down exactly what it is you want to do would help :)

---

### Post by TheHeathen on 2009-03-25
You're probably right - thanks - my first ever post - yes I want to share the mobile internet connection over a local lan network

---

### Post by inobe on 2009-03-25
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

all the information you could ever need :)

it's very definitive

---

### Post by inobe on 2009-03-25
my bad' i see a wireless card in your setup 

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

---

### Post by TheHeathen on 2009-03-27
Thanks for the links Inobe - got it working unencrypted sort of, just need some security now ;)

---

