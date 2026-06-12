---
title: "wpa_supplicant question: &quot;WPA group key update fails&quot; on Access Point"
date: 2006-03-23
forum: Networking &amp; Wireless
---

### Post by karon on 2006-03-23
I cannot get WPA to work on my laptop, and suspect that my wpa_supplicant.conf file is wrong. I assume that the wifi drivers and wpa_supplicant/madwifi works, based on the message "...WPA 4-way handshaking successes" in the AP event log (wifi also works in networks w/o WPA).

The wireless AP is a HP J8131A Wireless Access Point 420, and is configured to use WPA-PSK(TKIP).

Below is event log of AP and contents of my wpa_supplicant.conf.

Event log of wireless access point:
1 Mar 23 03:24:51 Information: WPA group key update fails at 00-12-79-3e-15-a5
2 Mar 23 03:24:47 Information: WPA 4-way handshaking successes at 00-12-79-3e-15-a5
3 Mar 23 03:24:47 Notice: 802.11g:Station Associated: 00-12-79-3e-15-a5
4 Mar 23 03:24:47 Notice: 802.11g:Station Authenticated: 00-12-79-3e-15-a5


Contents of wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="..."
        proto=WPA
        group=TKIP
        key_mgmt=WPA-PSK
        psk="......."
}

---

