---
title: "Constantly disconnected then reconnected [wired network]"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by qwallis on 2009-06-01
I have just done a fresh install of 9.04 and am being constantly disconnected and then re-connected on a wired network.

Any suggestions as to how to cure this would be very welcome (it's driving me nuts).

Many Thanks!

---

### Post by superprash2003 on 2009-06-01
check the LAN cable , it could be faulty

---

### Post by qwallis on 2009-06-01
> **superprash2003 said:**
> check the LAN cable , it could be faulty

The one I was using was new.
I have tried another one which I know to be OK and am still suffering constant disconnecting / reconnecting.


...waiting for a "reconnection window" so I can hit the "submit reply" button :(

---

### Post by Kamikaze_Gerbil on 2009-06-01
i have a similar problem, but it only happens a couple of times a day, for several minutes, then reconnects.

---

### Post by qwallis on 2009-06-01
The system log keeps spitting out the following....
I'm hoping that helps > 2009-06-01 19:42:14	my-desktop	kernel	[ 8270.888776] eth0: link down
2009-06-01 19:42:14	my-desktop	NetworkManager	<info>  (eth0): carrier now OFF (device state 8) 
2009-06-01 19:42:14	my-desktop	NetworkManager	<info>  (eth0): device state change: 8 -> 2 
2009-06-01 19:42:14	my-desktop	NetworkManager	<info>  (eth0): deactivating device (reason: 40). 
2009-06-01 19:42:15	my-desktop	NetworkManager	<info>  eth0: canceled DHCP transaction, dhcp client pid 1272 
2009-06-01 19:42:15	my-desktop	NetworkManager	<WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
2009-06-01 19:42:15	my-desktop	avahi-daemon[2466]	Withdrawing address record for 192.168.1.33 on eth0.
2009-06-01 19:42:15	my-desktop	avahi-daemon[2466]	Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
2009-06-01 19:42:15	my-desktop	avahi-daemon[2466]	Interface eth0.IPv4 no longer relevant for mDNS.
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  (eth0): carrier now ON (device state 2) 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  (eth0): device state change: 2 -> 3 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) starting connection 'Wired connection 1' 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  (eth0): device state change: 3 -> 4 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  (eth0): device state change: 4 -> 5 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
2009-06-01 19:42:16	my-desktop	kernel	[ 8272.555064] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  (eth0): device state change: 5 -> 7 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Beginning DHCP transaction. 
2009-06-01 19:42:16	my-desktop	dhclient	Internet Systems Consortium DHCP Client V3.1.1
2009-06-01 19:42:16	my-desktop	dhclient	Copyright 2004-2008 Internet Systems Consortium.
2009-06-01 19:42:16	my-desktop	dhclient	All rights reserved.
2009-06-01 19:42:16	my-desktop	dhclient	For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2009-06-01 19:42:16	my-desktop	dhclient	
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  dhclient started with pid 1343 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
2009-06-01 19:42:16	my-desktop	NetworkManager	<info>  DHCP: device eth0 state changed normal exit -> preinit 
2009-06-01 19:42:16	my-desktop	dhclient	Listening on LPF/eth0/00:c0:26:31:6b:78
2009-06-01 19:42:16	my-desktop	dhclient	Sending on   LPF/eth0/00:c0:26:31:6b:78
2009-06-01 19:42:16	my-desktop	dhclient	Sending on   Socket/fallback
2009-06-01 19:42:17	my-desktop	dhclient	DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
2009-06-01 19:42:17	my-desktop	dhclient	DHCPOFFER of 192.168.1.33 from 192.168.1.1
2009-06-01 19:42:17	my-desktop	dhclient	DHCPREQUEST of 192.168.1.33 on eth0 to 255.255.255.255 port 67
2009-06-01 19:42:17	my-desktop	dhclient	DHCPACK of 192.168.1.33 from 192.168.1.1
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>  DHCP: device eth0 state changed preinit -> bound 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>    address 192.168.1.33 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>    prefix 24 (255.255.255.0) 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>    gateway 192.168.1.1 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>    hostname 'dhcppc0' 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>    nameserver '192.168.1.1' 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
2009-06-01 19:42:17	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
2009-06-01 19:42:17	my-desktop	avahi-daemon[2466]	Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
2009-06-01 19:42:17	my-desktop	avahi-daemon[2466]	New relevant interface eth0.IPv4 for mDNS.
2009-06-01 19:42:17	my-desktop	avahi-daemon[2466]	Registering new address record for 192.168.1.33 on eth0.IPv4.
2009-06-01 19:42:17	my-desktop	dhclient	bound to 192.168.1.33 -- renewal in 98493 seconds.
2009-06-01 19:42:18	my-desktop	NetworkManager	<info>  (eth0): device state change: 7 -> 8 
2009-06-01 19:42:18	my-desktop	NetworkManager	<info>  Policy set 'Wired connection 1' (eth0) as default for routing and DNS. 
2009-06-01 19:42:18	my-desktop	NetworkManager	<info>  Activation (eth0) successful, device activated. 
2009-06-01 19:42:18	my-desktop	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
 


---

### Post by qwallis on 2009-06-02
](*,) As I don't have enough technical know-how, and it was a fresh install I thought I'd check one of the other distros :shock:
The problem doesn't show on openSuse, but that runs quite slow on my old box, so I'll burn a fresh disk and try installing Ubuntu again when I have some time over the weekend.

---

### Post by HeavyDC223 on 2011-12-08
My Lenovo ThinkPad R61i is having the same problem on Ubuntu 11.10 64bit.
It occurs only on the wired network. Wireless is working perfectly.
The wired network goes into a constant loop of disconnecting and reconnecting about once a second and continues until the cable is unplugged. This did not happen on 10.10 or 11.04 and does not happen in Windows 7 64bit on the same machine, cable and network. Selecting Link-Local Only or setting a static IP will allow it to remain connected, but any other setting results in a constant disconnect/reconnect loop that only stops when the cable is unplugged.

lspci gives this as the card model:
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

---

