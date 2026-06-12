---
title: "Cannot connect to accesspoint (wierd problem)"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by Double Trouble on 2011-06-20
Hello!
I'm trying to connect to an AP. I know the essid and the key both in hex and in ascii. So I write, as usual

```

# iwconfig wlan0 mode managed essid someessid key somehexkey

# dhclient wlan0

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

mon0: unknown hardware address type 803
mon0: unknown hardware address type 803
Listening on LPF/wlan0/00:11:22:33:44:55
Sending on   LPF/wlan0/00:11:22:33:44:55
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```



Please tell my of any reasons why it's not possible for me to connect to this AP. I can connect to other WEP- and WPA-encrypted networks so I think it must be something "wrong" with this particular network.

Any suggestions?

---

