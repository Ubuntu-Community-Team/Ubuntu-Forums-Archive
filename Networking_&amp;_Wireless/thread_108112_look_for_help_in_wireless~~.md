---
title: "look for help in wireless~~"
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by cooler813 on 2005-12-25
I tried my best to follow the howto guide in wiki but I failed...
My laptop is werid cuz it works on campus but doesnt work at home.
On campus it even works without essid, which means it detects the wireless itself. 
In my house, I am using a wireless router with WEP.
My laptop cannot detect any IP address
I got similar output as dissussed b4 by sudo dhclient
> There is already a pid file /var/run/dhclient.wlan0.pid with pid 0 
Internet Systems Consortium DHCP Client V3.0.2 Copyright 2004 Internet 
Systems Consortium. All rights reserved. For info, please visit 
[http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP) sit0: unknown hardware address type 776 
sit0: unknown hardware address type 776 Listening on 
LPF/wlan0/00:0f:b5:80:b6:d9 Sending on LPF/wlan0/00:0f:b5:80:b6:d9 
Sending on Socket/fallback DHCPDISCOVER on wlan0 to 255.255.255.255 port 
67 interval 5 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1 No 
DHCPOFFERS received. No working leases in persistent database - sleeping.

I type the password like XXXX-XXXX-XX
and ESSID is correct....
when I try PING, It cant ping anything....

Why there is a huge difference between school and home?

Cooler

---

### Post by Lambert on 2005-12-25
More information is needed.

card manufacture and model number. Driver if known

what are your wep settings. open or shared key. ascii or hexadecimal key

Some drivers require a configuration tweak for certain settings. For example, with the madwifi driver, wep and shared key the driver authmode has to be changed with this command iwpriv ath0 authmode 2 for it to work.

---

