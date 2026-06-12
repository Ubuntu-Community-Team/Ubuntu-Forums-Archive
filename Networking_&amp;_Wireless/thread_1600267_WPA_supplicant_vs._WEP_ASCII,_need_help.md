---
title: "WPA_supplicant vs. WEP ASCII, need help"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by NewUse on 2010-10-18
OS: Ubuntu 10.04 x64
```

Linux lubuntu 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

```

WiFi:  (Lenovo ThinkPad sl510):
```

 05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

```


mywep.conf:
```

ctrl_interface=/var/run/wpa_supplicant GROUP=wheel
network={
    ssid="mynet"
    key_mgmt=NONE
    wep_key0="72007"
    wep_tx_keyidx=0
}

```full log:
```

sudo wpa_supplicant -iwlan0 -c/etc/mywep.conf -dd
Initializing interface 'wlan0' conf '/etc/mywep.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/mywep.conf' -> '/etc/mywep.conf'
Reading configuration file '/etc/mywep.conf'
ctrl_interface='/var/run/wpa_supplicant GROUP=wheel'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=7):
     74 72 61 6e 5f 64 75 mynet
key_mgmt: 0x4
wep_key0 - hexdump(len=5): [REMOVED]
wep_tx_keyidx=0 (0x0)
Priority group 0
   id=0 ssid='mynet'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 70:1a:04:fc:5c:22
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 5b d4 8b b8 5c 9e 5f 2b b4 d9 58 24 5d 36 70 25
WPS: Build Beacon and Probe Response IEs
WPS: * Version
WPS: * Wi-Fi Protected Setup State (0)
WPS: * Version
WPS: * Wi-Fi Protected Setup State (0)
WPS: * Response Type (2)
WPS: * UUID-E
WPS: * Manufacturer
WPS: * Model Name
WPS: * Model Number
WPS: * Serial Number
WPS: * Primary Device Type
WPS: * Device Name
WPS: * Config Methods (0)
WPS: * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Cached scan results are empty - not posting
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Scan results did not fit - trying larger buffer (8192 bytes)
Received 7704 bytes of scan results (26 BSSes)
New scan results available
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS-AP-AVAILABLE
Selecting BSS from priority group 0
Try to find WPA-enabled AP

19: 40:4a:03:a7:76:fd ssid='mynet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE

19: 40:4a:03:a7:76:fd ssid='mynet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 40:4a:03:a7:76:fd ssid='mynet'
Trying to associate with 40:4a:03:a7:76:fd (SSID='mynet' freq=2442 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=1 seq_len=0 key_len=5
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 40:4a:03:a7:76:fd
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=40:4a:03:a7:76:fd
Associated with 40:4a:03:a7:76:fd
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 40:4a:03:a7:76:fd completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
^CCTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
ioctl[SIOCSIWAP]: Operation not permitted
ioctl[SIOCSIWESSID]: Operation not permitted
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
ioctl[SIOCSIWAP]: Operation not permitted
WEXT: Operstate: linkmode=0, operstate=6
```Please, help to locate trouble and fix it...

PS: sorry for my English

---

