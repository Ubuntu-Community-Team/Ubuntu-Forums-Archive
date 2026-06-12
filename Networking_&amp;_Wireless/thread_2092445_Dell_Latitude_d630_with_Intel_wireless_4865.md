---
title: "Dell Latitude d630 with Intel wireless 4865"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by Twistrjp on 2012-12-07
I am new to linux and Ubuntu. My work just gave me a free Dell latitude d630 with a intel wireless 4865.

I was trying to use network manager but had no luck and read that wicd was a good alternative. I got it to work 1 time then rebooted and it will not work again. I have read thread after thread and nothing is working. 

I have a fresh install of 12.04 and have all updates as well,  wired works fine

it sees the card, it connects but it will not obtain the IP address. below is log info. any help would be greatly appreciated 

2012/12/07 16:23:16 :: Internet Systems Consortium DHCP Client 4.1-ESV-R4
2012/12/07 16:23:16 :: Copyright 2004-2011 Internet Systems Consortium.
2012/12/07 16:23:16 :: All rights reserved.
2012/12/07 16:23:16 :: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
2012/12/07 16:23:16 :: 
2012/12/07 16:23:16 :: Listening on LPF/wlan0/00:21:5c:58:80:0d
2012/12/07 16:23:16 :: Sending on   LPF/wlan0/00:21:5c:58:80:0d
2012/12/07 16:23:16 :: Sending on   Socket/fallback
2012/12/07 16:23:16 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
2012/12/07 16:23:19 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
2012/12/07 16:23:22 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
2012/12/07 16:23:28 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
2012/12/07 16:23:34 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
2012/12/07 16:23:44 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
2012/12/07 16:24:05 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
2012/12/07 16:24:16 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
2012/12/07 16:24:33 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
2012/12/07 16:24:53 :: canceling connection attempt
2012/12/07 16:24:53 :: attempting to set hostname with dhclient
2012/12/07 16:24:53 :: using dhcpcd or another supported client may work better

---

### Post by Twistrjp on 2012-12-08
So i got it working. the issue was that 12.04 does not like WAP. my router does not have wap2 so i changed it to wep and worked NP

---

