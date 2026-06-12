---
title: "Wireless not starting automatically at boot"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by crabpot8 on 2012-08-10
Hey all, 

I'm running 12.04 server edition, and wireless is working fine except for one small snag - it doesn't seem to automatically connect wireless at boot. If I try dhclient at boot it hangs until Ctrl-C, and if I try service networking start I get "networking start/waiting". However, give it ~5 minutes after booting, and service networking start brings the wireless card right up. How do I go about debugging this -- I would like for the WiFi to start automatically.

Details:
foo@pooter:~$ lspci | grep ireless
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireles Network Adapter (PCI-Express) (rev 01)
foo@pooter:~$ cat /etc/network/interfaces 

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface wlan0 inet dhcp
	wpa-ssid <ssid removed>
	wpa-psk <psk removed>

The Wireless is WPA2 with TKIP+AES. I have the ability to change this if need be

---

### Post by chili555 on 2012-08-10
You haven't told it you want it to start automatically, so it doesn't. Please try:```
 The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="Red"]auto wlan0[/COLOR]
iface wlan0 inet dhcp
wpa-ssid <ssid removed>
wpa-psk <psk removed>

```By the way, in a server, why do you prefer DHCP instead of static?

---

