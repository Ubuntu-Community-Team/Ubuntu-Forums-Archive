---
title: "Bridge between eth0 and wlan0 , not working"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by vyruz18 on 2009-10-07
HI,
I have a small box running Ubuntu 9.04 server
Inside this box I Have 2 network cards:
- eth0:  3Com wired LAN card (Working fine)
- wlan0: LINksys WMP54G, which is identified as RAlink RT2500

The Linksys card gave me soume troubles  but I got it working using ndiswrapper.
I can now connect successfully to my Belkin wireless router using WPA security.

Now I'd like to make a bridge between eth0 and wlan0, the utlimate goal is to apply some pakket filtering (blocking certain ports) to this bridge.
But I figured I'd first try to get the bridge working, letting all data through, and once that works I'll start thinking about the filtering part..

Unfortunately I'm already stuck at the bridge part...

Without the bridge, my /etc/network/interfaces looks like this:
```

auto eth0
	iface eth0 inet dhcp
	
auto wlan0
	iface wlan0 inet dhcp
	wpa-driver wext
	wpa-ssid EGO_WIRELESS
	wpa-ap-scan 1
	wpa-proto WPA
	wpa-pairwise TKIP
	wpa-group TKIP
	wpa-key-mgmt WPA-PSK
	wpa-psk <passphrase generated from "wpa_passphrase" command)

```
This works fine and I get connection on both eth0 and wlan0

However, when I try to bridge, using this:
```

auto br0
	iface br0 inet static
	address 192.168.2.105
	netmask 255.255.255.0
	broadcast 192.168.2.255
	dns-nameservers 192.168.2.51
	bridge_ports eth0 wlan0
	bridge_fd 9
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off

```
It doesn't work...

Now I THINK I know whats wrong:
In the first example (without bridge) I have to specify what mi SSID, passphrase and other settings are.
In the 2nd example however (using br0), I can't specify what these settings must be.
I only don't know how to fix this...
Somehow I have to specify the WLAN parameters with the bridge settings, but I can't figure out how...

Thanks to anyone who can/wants to help...

---

