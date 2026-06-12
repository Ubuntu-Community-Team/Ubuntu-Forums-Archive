---
title: "Authentication problem, wpa_supplicant"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by parmenide on 2012-04-24
Good morning,

I have problem when trying to a WIFI network using wpa_supplicant, with ubuntu 11.10
I runned wpa_supplicant with the -dd option to get debug info.

I join my wpa_supplicant.conf and the output of the wpa_supplicant -dd command.


Thank you very much for your help !


 wpa_supplicant.conf:
----------------------

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1
network={
	ssid="myssid"
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP CCMP
	group=TKIP CCMP
	password="mypassword"
	psk="mypassword"
}


output of wpa_supplicant -dd
------------------------------


Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Scan results did not fit - trying larger buffer (8192 bytes)
Received 5573 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 0
0: 00:0b:3b:5a:61:00 ssid='myssid' wpa_ie_len=28 rsn_ie_len=26 caps=0x11
   selected based on WPA IE
Trying to associate with 00:0b:3b:5a:61:00 (SSID='myssid' freq=2422 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=15
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:0b:3b:5a:61:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0

---

