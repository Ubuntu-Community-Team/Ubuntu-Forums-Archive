---
title: "Can't connect to wireless network - wicd"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by boblettoj99 on 2013-03-25
Hi, I've been having problems lately with my wireless. For the last couple of months the wireless would cut out after a few hours of the laptop being on, then I'd have to restart it and it would work again.

However this time it hasn't come back.

I got fed up of network-manager and tried installing wicd instead which gives me a little more information, but it still won't connect.

The wicd log is as follows:

> 2013/03/26 00:34:45 :: Connecting to wireless network SKY9CCC3
2013/03/26 00:34:45 :: attempting to set hostname with dhclient
2013/03/26 00:34:45 :: using dhcpcd or another supported client may work better
2013/03/26 00:34:46 :: attempting to set hostname with dhclient
2013/03/26 00:34:46 :: using dhcpcd or another supported client may work better
2013/03/26 00:34:46 :: Putting interface down
2013/03/26 00:34:46 :: Releasing DHCP leases...
2013/03/26 00:34:46 :: attempting to set hostname with dhclient
2013/03/26 00:34:46 :: using dhcpcd or another supported client may work better
2013/03/26 00:34:46 :: Setting false IP...
2013/03/26 00:34:46 :: Stopping wpa_supplicant
2013/03/26 00:34:46 :: Flushing the routing table...
2013/03/26 00:34:46 :: Putting interface up...
2013/03/26 00:34:48 :: Generating psk...
2013/03/26 00:34:48 :: Attempting to authenticate...
2013/03/26 00:35:24 :: wpa_supplicant authentication may have failed.
2013/03/26 00:35:24 :: connect result is Failed
2013/03/26 00:35:24 :: exiting connection thread
2013/03/26 00:35:24 :: Sending connection attempt result bad_pass
2013/03/26 00:35:24 :: attempting to set hostname with dhclient
2013/03/26 00:35:24 :: using dhcpcd or another supported client may work better
2013/03/26 00:35:24 :: attempting to set hostname with dhclient
2013/03/26 00:35:24 :: using dhcpcd or another supported client may work better

It recognises the wireless card fine:
>   *-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: e0:b9:a5:dc:f7:96
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.0.0-32-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:e000(size=256) memory:f7d00000-f7d03fff


Any idea what I can do? My ubuntu version is 11.10

---

### Post by audunpoi on 2013-03-26
Did you: 
-Purge anything related to Network Manager
- set wlan0 : wicd -> preferences -> Network Interfaces -> Wireless interface: wlan0

?

---

