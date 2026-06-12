---
title: "WPA Wireless inet /etc/network/interfaces"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by roop_s on 2011-03-26
I'd like to set the wireless config in /etc/network/interface and not use any GUI tools. Why? This wireless interface is going to pass traffic from the wireless to wired ethernet and needs static IPs. NM-APPLET works nice but doesn't take a static IP without default gateway. The default gateway exists on a wired interface. I put this in /etc/network/interface:

auto wlan0
iface wlan0 inet static
address 192.168.2.5
netmask 255.255.255.0
wpa-ssid "linksys"
wpa-psk "wpa-key"

This is the wireless controller:
01:08.0 Network controller: RaLink RT2500 802.11g (rev 01)
	Subsystem: ASUSTeK Computer Inc. WL-130g
	Flags: bus master, slow devsel, latency 32, IRQ 18
	Memory at e0004000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: rt2500pci
	Kernel modules: rt2500pci

The result is this. Note it's missing the "RUNNING" part and doesn't actually send/receive any traffic.
wlan0     Link encap:Ethernet  HWaddr 00:11:2f:37:21:83  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12430 (12.4 KB)  TX bytes:2325 (2.3 KB)

Again NM-APPLET works fine in GUI mode but this system is going to be unmanned and needs to take reboots without an prompt for WPA key or which AP to select.

Any recommendations on how I can achieve this would be appreciated.

---

