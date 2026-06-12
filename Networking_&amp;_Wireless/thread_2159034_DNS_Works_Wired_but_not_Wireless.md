---
title: "DNS Works Wired but not Wireless"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by rlsj on 2013-07-01
Ubuntu 12.04 on Acer Aspire 9300 portable: Can access the Internet with known IPs or domain names using the wired adaptor, but only with known IPs on the wireless adaptor: i.e., DNS access does not seem to work using wireless.  A command such as "ping sdf.lonestar.org" hangs without response in a wireless connection but returns an IP and performs packet exchanges in a wired connection.

The modem is an ATT Uverse 3801HGV by 2Wire, Inc., which includes a Wi-Fi router.  I can connect through it wirelessly to the Internet, using known IP addresses, but not if using DNS.  I have tried substituting the IPs of a known DNS for the modem default (192.168.1.254) with no advantage.

I want to use this laptop elsewhere in the house.  Would appreciate any suggestions.

--rlsj

---

### Post by steeldriver on 2013-07-01
Where are you inserting the substitute DNS IP exactly? on the modem/router or in the IPv4 settings for the wireless connection?

Are you sure you have the wireless connection set up to get its DNS as well as its IP address via DHCP (i.e. from the modem/router) - i.e. 'Automatic (DHCP)' not 'Automatic (DHCP) addresses only'?

---

### Post by rlsj on 2013-07-02
Here is the "Connection Information" currently reported for wireless:

Interface:        802.11 WiFi (wlan0)
Hardware Address:    [Redacted]
Driver:            ath5k
Speed:            48 Mb/s
Security:        None

IPv4
IP Address:        192.168.1.65
Broadcast Address:    192.168.1.255
Subnet Mask:        255.255.255.0
Default Route:        192.168.1.254
Primary DNS:        127.0.0.1
Secondary DNS:        192.168.1.254

IPv4 Settings (Edit):    Automatic (DHCP)
(No addresses, no DNS servers, no Search domain, no DHCP client ID)

***
Interesting discovery: If I reconnect the Ethernet cable (which automatically re-enables the wired connection) but again disable the wired connection, leaving wireless enabled, now the _wireless_ DNS works!  If I then disconnect the Ethernet cable, wireless DNS stops working (ping <domain> hangs as before).  Apparently DNS resolves through the Ethernet line if it's connected regardless of the wireless state.  Unfortunately this doesn't help operation elsewhere in the house.

Thanks for your attention.

---

