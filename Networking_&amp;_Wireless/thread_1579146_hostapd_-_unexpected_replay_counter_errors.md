---
title: "hostapd - unexpected replay counter errors"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by clonek on 2010-09-21
I'm getting repeated errors in my syslog after installing hostapd.

I have a ubuntu box setup as a router/firewall with a wireless card acting as a wireless access point. The access point is using hostapd to provide WPA for wireless connections.

I received these errors every 5-10 minutes almost exactly.

Sep 21 06:55:19 localhost hostapd: ath0: STA 38:e7:d8:e8:5e:98 WPA: group key handshake completed (RSN)
Sep 21 06:55:19 localhost hostapd: ath0: STA 38:e7:d8:e8:5e:98 WPA: received EAPOL-Key 2/2 Group with unexpected replay counter

my hostapd.conf:

driver=madwifi
interface=ath0
bridge=br0
hw_mode=g
ssid=wifi
wpa=3
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
wpa_passphrase=itsasecret

lspci for wireless card:
01:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

The wireless connection works fine, my logs are just filling up with this error.

Can anyone help?

---

