---
title: "Wifi cuts out with HP WLAN 500"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by gordon142 on 2009-09-14
Connected to my home network (802.11g/WPA), the wireless connection cuts out about every 5 minutes when running on Ubuntu 9.04. It usually takes about 30 seconds to reconnect.

The card (HP WLAN W500):
02:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

        Subsystem: Compaq Computer Corporation Device 00e5

        Flags: bus master, medium devsel, latency 168, IRQ 11

        Memory at 90080000 (32-bit, non-prefetchable) [size=64K]

        Capabilities: [44] Power Management version 2

        Kernel driver in use: ath5k_pci

        Kernel modules: ath_pci, ath5k


I have tried both the default ath5k driver and the proprietary madwifi driver, and both exhibit exactly the same issue.

Interestingly, a default install of Ubuntu 9.04 from the latest stable ISO does NOT have this issue - the wireless works perfectly. It is only after installing all available updates that it stops working properly.

Log excerpt from when the network is reconnecting:

> 45 gordon-hp NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Sep 14 16:50:45 gordon-hp kernel: [ 1221.060870] wlan0: authenticate with AP 00:1c:b3:ab:d5:2b
Sep 14 16:50:45 gordon-hp kernel: [ 1221.061026] wlan0: authenticate with AP 00:1c:b3:ab:d5:2b
Sep 14 16:50:45 gordon-hp kernel: [ 1221.062775] wlan0: authenticated
Sep 14 16:50:45 gordon-hp kernel: [ 1221.062785] wlan0: associate with AP 00:1c:b3:ab:d5:2b
Sep 14 16:50:45 gordon-hp kernel: [ 1221.066676] wlan0: RX AssocResp from 00:1c:b3:ab:d5:2b (capab=0x431 status=0 aid=3)
Sep 14 16:50:45 gordon-hp kernel: [ 1221.066685] wlan0: associated
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Gordon Wifi'. 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Sep 14 16:50:45 gordon-hp dhclient: Internet Systems Consortium DHCP Client V3.1.1
Sep 14 16:50:45 gordon-hp dhclient: Copyright 2004-2008 Internet Systems Consortium.
Sep 14 16:50:45 gordon-hp dhclient: All rights reserved.
Sep 14 16:50:45 gordon-hp dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Sep 14 16:50:45 gordon-hp dhclient: 
Sep 14 16:50:45 gordon-hp dhclient: wmaster0: unknown hardware address type 801
Sep 14 16:50:45 gordon-hp dhclient: wmaster0: unknown hardware address type 801
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  dhclient started with pid 4477 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Sep 14 16:50:45 gordon-hp dhclient: Listening on LPF/wlan0/00:0b:cd:59:27:1d
Sep 14 16:50:45 gordon-hp dhclient: Sending on   LPF/wlan0/00:0b:cd:59:27:1d
Sep 14 16:50:45 gordon-hp dhclient: Sending on   Socket/fallback
Sep 14 16:50:45 gordon-hp dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep 14 16:50:45 gordon-hp dhclient: DHCPOFFER of 10.0.1.3 from 10.0.1.1
Sep 14 16:50:45 gordon-hp dhclient: DHCPREQUEST of 10.0.1.3 on wlan0 to 255.255.255.255 port 67
Sep 14 16:50:45 gordon-hp dhclient: DHCPACK of 10.0.1.3 from 10.0.1.1
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>    address 10.0.1.3 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>    prefix 24 (255.255.255.0) 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>    gateway 10.0.1.1 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>    nameserver '10.0.1.1' 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Sep 14 16:50:45 gordon-hp NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Sep 14 16:50:45 gordon-hp avahi-daemon[2754]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.1.3.
Sep 14 16:50:45 gordon-hp avahi-daemon[2754]: New relevant interface wlan0.IPv4 for mDNS.
Sep 14 16:50:45 gordon-hp avahi-daemon[2754]: Registering new address record for 10.0.1.3 on wlan0.IPv4.
Sep 14 16:50:45 gordon-hp dhclient: bound to 10.0.1.3 -- renewal in 6287 seconds.
Sep 14 16:50:46 gordon-hp NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Sep 14 16:50:46 gordon-hp NetworkManager: <info>  Policy set 'Auto Gordon Wifi' (wlan0) as default for routing and DNS. 
Sep 14 16:50:48 gordon-hp ntpdate[4536]: adjust time server 91.189.94.4 offset 0.044908 sec
Sep 14 16:51:32 gordon-hp NetworkManager: <debug> [1252972292.003977] periodic_update(): Roamed from BSSID 00:1C:B3:AB:D5:2B (Gordon Wifi) to (none) ((none)) 

Anyone have any suggestions? This is driving me crazy.

---

### Post by JakP on 2009-09-14
Don't know if this helps but had same problem and reducing my wireless rate and MTU stabalised it significantly.

---

