---
title: "Can't get eth0 to connect, help with log please"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by nabab on 2011-06-22
Hey there,

I have a 10.04 box connected to a router with DHCP and wireless. Lathough it can connect through the wifi, I can't get the connection working with the ethernet cable (which is the one I wanna use by default).
Can someone have a look at this little syslog extract and tell me what I can't see please?

```
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) starting connection 'Auto Ethernet'
Jun 22 16:21:29 KarlData NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 22 16:21:29 KarlData NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 22 16:21:29 KarlData NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jun 22 16:21:29 KarlData NetworkManager: <info>  dhclient started with pid 15351
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jun 22 16:21:29 KarlData NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun 22 16:21:29 KarlData dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun 22 16:21:29 KarlData dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun 22 16:21:29 KarlData dhclient: All rights reserved.
Jun 22 16:21:29 KarlData dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 22 16:21:29 KarlData dhclient: 
Jun 22 16:21:29 KarlData NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jun 22 16:21:29 KarlData dhclient: Listening on LPF/eth0/00:1d:60:b2:cd:e3
Jun 22 16:21:29 KarlData dhclient: Sending on   LPF/eth0/00:1d:60:b2:cd:e3
Jun 22 16:21:29 KarlData dhclient: Sending on   Socket/fallback
Jun 22 16:21:33 KarlData dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jun 22 16:21:39 KarlData dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jun 22 16:21:45 KarlData dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 22 16:21:52 KarlData dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jun 22 16:22:03 KarlData dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jun 22 16:22:15 KarlData NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Jun 22 16:22:15 KarlData NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 15351
Jun 22 16:22:15 KarlData NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun 22 16:22:15 KarlData NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun 22 16:22:15 KarlData NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Jun 22 16:22:15 KarlData NetworkManager: <info>  Marking connection 'Auto Ethernet' invalid.
Jun 22 16:22:15 KarlData NetworkManager: <info>  Activation (eth0) failed.
Jun 22 16:22:15 KarlData NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun 22 16:22:15 KarlData NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Jun 22 16:22:15 KarlData NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Jun 22 16:22:15 KarlData NetworkManager: <info>  Policy set 'Auto Thor' (wlan0) as default for routing and DNS.
```

Edit:
I may add that it's the default auto connection, but I've also tried to create one manually setting the right ip address, gateway, etc, and attributing the same ip on the router to the MAC address of the card. I've also tried to edit manually the interfaces file, with no effect, or no good one at least. This log comes from a moment when nothing has been changed from the original 10.04 installation.

And I have connected a laptop to this very same cable, and the connection worked straight away...

Thanks!

---

### Post by RoflHaxBbq on 2011-06-24
Open '/etc/network/interfaces' in your text editor of choice.

Make sure it reads:

allow-hotplug eth0
iface eth0 inet dhcp

OR

auto eth0
iface eth0 inet dhcp

---

