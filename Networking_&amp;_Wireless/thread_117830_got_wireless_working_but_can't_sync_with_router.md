---
title: "got wireless working but can't sync with router"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by kasemodz on 2006-01-15
Alright I installed my realtek rtl8185 chipset using ndiswrapper. now my wireless connection is in the networking section. I went there and activated my wireless by providing my Essid. It activates it however it takes a long time. Then i went to ifconfig eth0 and it doesn't display my ip address. Thus for some reason i can't connect to my router. Any possible solutions?

---

### Post by kasemodz on 2006-01-15
alright I tried to do more digging and orignally my /etc/network/interfaces had this setup for wlan0 > iface wlan0 inet dhcp
wireless-essid SMC Wireless I added > auto wlan0
Basically when I do > sudo ifup wlan0 I get this stuff
> There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0e:2e:6d:76:1f
Sending on   LPF/wlan0/00:0e:2e:6d:76:1f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I know the router is functioning properly so it must be the card.

Also when i do dmesg, I get this stuff
> [4302876.884000] wlan0: no IPv6 routers present
[4302907.538000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4302917.834000] eth0: no IPv6 routers present
[4303002.999000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303002.999000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303003.049000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303003.049000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303003.180000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303003.180000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303003.230000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).


---

### Post by kasemodz on 2006-01-15
anyone, I think ipv6 has something messed up with it.

---

