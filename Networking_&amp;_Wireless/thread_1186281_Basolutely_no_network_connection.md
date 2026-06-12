---
title: "Basolutely no network connection"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by thenotwist on 2009-06-13
Hi,

I've got a really weird thing going on with my wired network connection. A few days ago it stopped working entirely.

I was running Intrepid on my box but I decided to install a copy of WinXP Home, too so my girlfriend could play some games. In Windows I disabled the ethernet connection and before rebooting enabled it again because I didn't want some programs to access the internet.

When I booted back into Intrepid all of a sudden there was no network connection whatsoever. My router does not respond to any DHCPDISCOVERs, it doesn't answer to any packets broadcasted over the network. I tried using a live CD, I installed Jaunty from scratch but it was no use either.

Funny thing is, in Windows it works like a charme, no problems of any kind, everything's the way it should be. I did a hard reset on my router but that didn't work out either. When I try to assign a static IP address in Jaunty it tells me that ethernet is now connected, but it actually isn't. The gateway always changes back to 0.0.0.0 as soon as I close the Network Manager Applet and route outputs

```
192.168.2.0 * 255.255.255.0 1 0 0 eth0
```

plus the entry for the loopback interface.
I've already tried several fixes suggested here and other places like changing dhclient.conf, the Network Manager settings to managed=true, added iface eth0 inet dhcp to /etc/network/interfaces as well as a static entry but it all didn't work.

dhcclient outputs DHCPDISCOVER timeouts over and over and when I use a static IP it says that everything's fine, but nothing actually works... my router's lights don't even blink or light up as they do when I'm using windows...

I'm using the 8139too driver, this is NetworkManager's ouput:
```

philipp@booster:~$ sudo NetworkManager --no-daemon
sudo: unable to resolve host booster
NetworkManager: <info>  starting...
NetworkManager: <info>  eth0: driver is '8139too'.
NetworkManager: <info>  Found new Ethernet device 'eth0'.
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_0c_76_8c_9d_78
NetworkManager: <info>  (eth0): device state change: 1 -> 2
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device (reason: 2).
NetworkManager: <info>  (eth0): carrier now ON (device state 2)
NetworkManager: <info>  (eth0): device state change: 2 -> 3
NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
NetworkManager: <info>  (eth0): device state change: 3 -> 4
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (eth0): device state change: 4 -> 5
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (eth0): device state change: 5 -> 7
NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

NetworkManager: <info>  dhclient started with pid 7127
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Listening on LPF/eth0/00:0c:76:8c:9d:78
Sending on   LPF/eth0/00:0c:76:8c:9d:78
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it.
NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 7127
NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
NetworkManager: <info>  (eth0): device state change: 7 -> 9
NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
NetworkManager: <info>  Activation (eth0) failed.
NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
NetworkManager: <info>  (eth0): device state change: 9 -> 3
NetworkManager: <info>  (eth0): deactivating device (reason: 0).

```

I really don't know where to go from here, so it'd be awesome if somebody could give me a hand with this, any tips are appreciated.

---

