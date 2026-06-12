---
title: "Please help my wireless DHCP problem"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by stryderjzw on 2006-05-06
Hi,

I just moved to Waterloo for an 8 month co-op workterm and am living in a shared accomodation.  I can't get wireless working and I really need it to talk to family and friends!

Here's what I get when I run ifup eth0:  (eth0 is my wireless...)
```

Starting wpa_supplicant: ioctl[SIOCSIWPMKSA]: Operation not supported
done.
There is already a pid file /var/run/dhclient.eth0.pid with pid 12719
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:04:23:5f:d6:48
Sending on   LPF/eth0/00:04:23:5f:d6:48
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

As you can see, I am using WPA... but this works because I've done a test:
```

stryderjzw@stryderjzw:/usr/sbin$ sudo ./wpa_supplicant -Dipw -c/etc/wpa_supplicant.conf -ieth0 -w
ioctl[SIOCSIWPMKSA]: Operation not supported
Trying to associate with 00:0c:41:cd:3a:53 (SSID='tsunami' freq=0 MHz)
Associated with 00:0c:41:cd:3a:53
WPA: Key negotiation completed with 00:0c:41:cd:3a:53 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:0c:41:cd:3a:53 completed (auth)
WPA: Group rekeying completed with 00:0c:41:cd:3a:53 [GTK=TKIP]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

I can get internet working with wired, but my landlord has to drag a line around the house and I don't get to watch tv!

Please, Please, PLease help!  It's tough being tied to a wire!  :p 

Thanks!

---

### Post by stryderjzw on 2006-05-08
Well, I've been at it for another while, but no results.  Anyone have any good ideas?

---

