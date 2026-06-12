---
title: "Wifi Radar"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by comradejanus on 2009-03-31
Hi, im trying to connect to my wireless network using wifi radar,

I try connecting to my home network but when I do I get the following in the console:

[PHP]Error for wireless request "Set Nickname" (8B1C) :
    SET failed on device wlan0 ; Operation not supported.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:b5:2d:db
Sending on   LPF/wlan0/00:21:63:b5:2d:db
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13[/PHP]

What does this mean? and how do I fix it?

lspci -v gives me:

[PHP]02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7131
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k, ath_pci[/PHP]

Oh and im using ubuntu 8.10.

Thanks for any help

---

