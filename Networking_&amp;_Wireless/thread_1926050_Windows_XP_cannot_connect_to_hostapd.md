---
title: "Windows XP cannot connect to hostapd"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by dredkin on 2012-02-15
Hi All!
I've got an installation of ubuntu server 11.10 (x86, kernel 3.0.0-15).
I'm trying to set up a Wi-Fi access point. I've got ASUS AT3IONT-I deluxe mobo with builtin wifi card. This is what lspci -v shows :
```
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: AzureWave Device 1089
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
        Capabilities: [170] Power Budgeting <?>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```First I've made a bridge of my eth0 and wlan0. This is my /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo br0 eth0 wlan0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
#       address 192.168.1.119
#       netmask 255.255.255.0
#       gateway 192.168.1.1
#       network 192.168.1.0

#Wireless Setup
iface wlan0 inet manual

#Bridge interface
iface br0 inet static
        address 192.168.1.119
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        bridge_ports eth0 wlan0
        gateway 192.168.1.1

```I've installed hostapd. This is my hostapd.conf
```
interface=wlan0
driver=nl80211
bridge=br0
ssid=my-wifi
hw_mode=g
country_code=RU
channel=1

macaddr_acl=0

wpa=1
wpa_key_mgmt=WPA-PSK
wpa_passphrase=password
wpa_pairwise=TKIP

logger_syslog=-1
logger_syslog_level=0
logger_stdout=-1
logger_stdout_level=0

```Now I'm trying to connect here from acer notebook with Windows XP and Asus PCM wifi card (chipset is Ralink RT2500).
When I set wpa=0 (open system), client connects with no problem, and all works well. But when I try to enable wpa (i've tried both wpa=1 and wpa=3, also wpa_pairwise=TKIP and CCMP) connection is just droppped and syslog is
```

Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: authentication OK (open system)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 MLME: MLME-AUTHENTICATE.indication(00:1e:8c:50:55:41, OPEN_SYSTEM)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 MLME: MLME-DELETEKEYS.request(00:1e:8c:50:55:41)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: authenticated
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: association OK (aid 1)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: did not acknowledge association response
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: authentication OK (open system)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: event 0 notification
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 MLME: MLME-AUTHENTICATE.indication(00:1e:8c:50:55:41, OPEN_SYSTEM)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 MLME: MLME-DELETEKEYS.request(00:1e:8c:50:55:41)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: authenticated
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: association OK (aid 1)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: associated (aid 1)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 MLME: MLME-ASSOCIATE.indication(00:1e:8c:50:55:41)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 MLME: MLME-DELETEKEYS.request(00:1e:8c:50:55:41)
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: event 1 notification
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: start authentication
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.1X: unauthorizing port
Feb 16 00:09:11 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: sending 1/4 msg of 4-Way Handshake
Feb 16 00:09:12 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: EAPOL-Key timeout
Feb 16 00:09:12 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: sending 1/4 msg of 4-Way Handshake
Feb 16 00:09:13 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: EAPOL-Key timeout
Feb 16 00:09:13 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: sending 1/4 msg of 4-Way Handshake
Feb 16 00:09:14 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: EAPOL-Key timeout
Feb 16 00:09:14 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: sending 1/4 msg of 4-Way Handshake
Feb 16 00:09:15 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 WPA: EAPOL-Key timeout
Feb 16 00:09:15 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.1X: unauthorizing port
Feb 16 00:09:15 redkin-server hostapd: wlan0: STA 00:1e:8c:50:55:41 IEEE 802.11: deauthenticated due to local deauth request

```Help me, ubuntu gurus, what did I do wrong?:confused:

---

