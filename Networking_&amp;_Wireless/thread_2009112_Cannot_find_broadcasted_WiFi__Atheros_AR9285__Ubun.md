---
title: "Cannot find broadcasted WiFi | Atheros AR9285 | Ubuntu12.04"
date: 2012-06-24
forum: Networking &amp; Wireless
---

### Post by pd12 on 2012-06-24
I can connect to the Ad-hoc IPv4 shared Wifi on my laptop (Samsung R580 - JS02AU)
However, I cannot find the broadcasted network on any of my wireless devices (phones, tablets etc.) even if I input the SSID and security codes, my devices won't connect.

I am using the GUI method here:
[https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing#GUI_Method_via_Network_Manager_.28Ubuntu_12.04.29](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing#GUI_Method_via_Network_Manager_.28Ubuntu_12.04.29)

I did try to follow this:
[http://nagaraj-embedded.blogspot.com.au/2012/03/how-to-share-your-ethernet-over-wifi.html](http://nagaraj-embedded.blogspot.com.au/2012/03/how-to-share-your-ethernet-over-wifi.html)
I was able to get my devices to see and connect to the broadcasted network but the devices couldn't get onto the internet. 


System details:
Samsung R580 - JS02AU
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
Ubuntu12.04
Kernel: 3.2.0-25-generic x86_64
Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)

Note: I was never able to use this GUI method to share my ethernet internet over the wifi on any previous distributions either (10.04 - 11.10)

Any pointers would be greatly appreciated!
I don't want to do any intensive text based procedures like the blogspot link above, because I don't really know what I'm doing and somehow lost connection to the internet once when I restarted dhcpd and it said something about eth0 not having any subnet or directed connections.

---

