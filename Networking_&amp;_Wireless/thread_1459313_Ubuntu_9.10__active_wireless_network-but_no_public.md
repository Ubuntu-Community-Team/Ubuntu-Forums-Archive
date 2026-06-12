---
title: "Ubuntu 9.10 : active wireless network-but no public connection."
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by dalpets on 2010-04-21
I have just installed 9.10(32bit)using the Edimax ew7318ug wireless usb dongle. According to the sticky compatibles this dongle should work out of the box. I tried it on 8.04.1 without any success. It works for Mandriva 9 on the same partioned drive as Ubuntu 9.10.

I have an active network connection (80-82%) but no internet connection.
I have tried to set up a static manual address for a connection to my network router.

The active connection returns the following information;

Interface: 802.11 Wifi (Wlan0)
hardware address: 00:0E:2E:CE:97:12 (my ew7318 usb dongle)
driver: rt73usb
speed: 48mb/s
security:WPA/WPA2
IP address: 192.168.1.32
broadcast: 192.168.1.255
subnet mask: 255.255.255.0
MTU:1500
mode: infrastructure
.......................
The WPA security passwd & SSID is set up as for my other computers on the network.
When I complete the IPV4 settings I try and fill in the gateway with my network router IP viz., 192.168.1.1 but it reverts to 0.0.0.0
In the config section for primary DNS/Domain I have tried using 192.168.1.1 there, without any domain and without any success.

So I have a problem not being able to record the IP address of my network router. I have configured the BSSID (being the MAC address of my router) but I doubt if that achieves the same thing as the router IP which, as I said, I can't configure.

Any help as to why I can't get past the router would be appreciated

---

