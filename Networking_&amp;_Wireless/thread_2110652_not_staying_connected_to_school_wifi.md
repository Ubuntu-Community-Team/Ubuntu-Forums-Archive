---
title: "not staying connected to school wifi"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by Benjamindaines on 2013-01-30
I'm having trouble with keeping my laptop connected to my school's secure network.  It uses PEAP / MSCHAPV2 authentication and has multiple routers spread out all over the campus.  Two issues I'm experiencing is the wireless card will roam from one BBSID to another, causing it to disconnect whenever it decides to talk to another router.  I have "solved" this by manually entering the BBSID into the network settings.  But I am still experiencing dropped connections.  Leading up to the drop the connection gets very slow, then stops responding all together, then I'm disconnected.  Here's a log read out. 

```
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<warn> (wlan0): link timed out.
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): device state change: activated -> failed (reason 'supplicant-timeout') [100 120 11]
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<warn> Activation (wlan0) failed for connection 'tusecurewireless'
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): deactivating device (reason 'none') [0]
01/30/13 06:31:15 PM	ubuntu	kernel	[ 4020.303274] wlan0: authentication with 00:0c:e6:02:88:07 timed out
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): canceled DHCP transaction, DHCP client pid 16859
01/30/13 06:31:15 PM	ubuntu	avahi-daemon[1797]	Withdrawing address record for fe80::e6ce:8fff:fe3e:15a on wlan0.
01/30/13 06:31:15 PM	ubuntu	avahi-daemon[1797]	Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::e6ce:8fff:fe3e:15a.
01/30/13 06:31:15 PM	ubuntu	avahi-daemon[1797]	Interface wlan0.IPv6 no longer relevant for mDNS.
01/30/13 06:31:15 PM	ubuntu	kernel	[ 4020.491511] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
01/30/13 06:31:15 PM	ubuntu	avahi-daemon[1797]	Withdrawing address record for 10.109.25.213 on wlan0.
01/30/13 06:31:15 PM	ubuntu	avahi-daemon[1797]	Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.109.25.213.
01/30/13 06:31:15 PM	ubuntu	avahi-daemon[1797]	Interface wlan0.IPv4 no longer relevant for mDNS.
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): supplicant interface state: authenticating -> disconnected
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): supplicant interface state: disconnected -> scanning
01/30/13 06:31:15 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): supplicant interface state: scanning -> disconnected
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) starting connection 'tusecurewireless'
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0/wireless): access point 'tusecurewireless' has security, but secrets are required.
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0/wireless): connection 'tusecurewireless' has security, and secrets exist.  No new secrets needed.
01/30/13 06:31:18 PM	ubuntu	NetworkManager[1861]	<info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
01/30/13 06:31:20 PM	ubuntu	NetworkManager[1861]	<info> (wlan0): supplicant interface state: disconnected -> scanning

```

---

### Post by Benjamindaines on 2013-01-30
I may have fixed it.  I was being an idiot and using old instructions for setting up the card (b43 installer rather than linux-firmware-nonfree).  Seems to be working very well on my apartment wifi (which is set up the same with multiple routers, but without the encryption.)  I'll report back tomorrow once I'm on campus again. Oops.

---

