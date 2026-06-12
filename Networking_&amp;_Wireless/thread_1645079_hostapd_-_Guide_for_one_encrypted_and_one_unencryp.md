---
title: "hostapd - Guide for one encrypted and one unencrypted network?"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by harfagre on 2010-12-14
Hi everyone!
I was just wondering if anyone here knows of a step-by-step guide for setting up a solution like the one I am after for my hostapd-AP:

[B]1. One encrypted WLAN SSID that grants access to both my internal home network and the Internet (for my personal use only)

2. One unencrypted WLAN SSID available to anyone but that will only grant access to the Internet, not my private LAN (my AP acting as an AP and a firewall at the same time)[/B]

With the setup below I have managed to create one encrypted and one unecrypted SSID and I can connect to both of them. The problem is that my current solution is based on bridging the SSID's to my wired ethernet-interface, via which the traffic is then routed onto the Internet:

**HOSTAPD CONFIG**
interface=wlan0
bridge=br0
driver=nl80211
ssid=ENCRYPTED_INTERNET_AND_LAN_ACCESS
channel=6
hw_mode=g
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=presharedkey
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
bss=wlan0_0
bssid=02:22:43:66:21:4d
ssid=UNENCRYPTED_INTERNET_ACCESS_ONLY

**SOFTWARE VERSIONS**
hostapd v0.8.x/Ubuntu 10.04.1 LTS/Linux 2.6.32-24-generic

This means that users of my unencrypted, free-to-use WLAN-network will be in the same switched network (broadcast domain) as my private WLAN. A user of my open network will only need to change his IP-adress to fit my LAN subnet in order to be able to open a connection to my PC's. I suppose that what I am after is a VLAN-based solution that can separate my private WLAN from my public on the data link-layer.
[B]
Is there a guide somewhere that addresses what I'm after? Thanks![/B]

---

