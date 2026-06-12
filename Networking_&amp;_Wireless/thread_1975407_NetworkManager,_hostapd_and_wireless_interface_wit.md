---
title: "NetworkManager, hostapd and wireless interface with static IP"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by teel on 2012-05-07
Hi,
Is there any way that NetworkManager allows me to set up the static IP for the wlan1 interface in order to prepare it for hostapd? I created the configuration entry for “Wireless connection 1”, set up static IP (192.168.0.1) with netmask (255.255.255.0) and gw (0.0.0.0), Infrastructure mode, SSID “test”. I expected it to set this up regardless of whether it’s connected to this nonexisting “test” network or not, then the hostapd was meant to do the rest, i.e set to Master mode. No luck: hostapd sets up correctly, but I don’t have the IP address of wlan1.

Best Regards
teel

---

