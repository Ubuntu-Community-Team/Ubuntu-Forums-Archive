---
title: "ndiswrapper + wpa_supplicant association lost"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by salvatore001 on 2010-09-22
hi

i'm unable to connect with wpa encryption to my AP.
i have tried many configurations found in the forums and even upgraded the distribution. currentyle 10.04.1 running.

here are the logs

iwslist wlan0 scan
```

wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:73:0A:42
                    ESSID:"salvattore001"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```


ndiswrapper -l
```


netmw225 : driver installed
	device (1286:1FAB) present
```

cat /etc/wpa_supplicant.conf
```

ap_scan=1
#eapol_version=2
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="salvattore001"
    key_mgmt=WPA-PSK
    proto=WPA RSN
    pairwise=CCMP TKIP
    group=CCMP TKIP
    psk="REMOVED"
}

```

sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -dd
```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=13):
     73 61 6c 76 61 74 74 6f 72 65 30 30 31            salvattore001   
key_mgmt: 0x2
proto: 0x2
pairwise: 0x18
group: 0x18
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='salvattore001'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 08:10:74:07:40:94
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): c8 e6 9b a4 13 cd 50 79 ab 75 23 ae 25 72 2b 05
WPS: Build Beacon and Probe Response IEs
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Response Type (2)
WPS:  * UUID-E
WPS:  * Manufacturer
WPS:  * Model Name
WPS:  * Model Number
WPS:  * Serial Number
WPS:  * Primary Device Type
WPS:  * Device Name
WPS:  * Config Methods (0)
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 782 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:21:29:73:0a:42 ssid='salvattore001' wpa_ie_len=22 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:21:29:73:0a:42 ssid='salvattore001'
Trying to associate with 00:21:29:73:0a:42 (SSID='salvattore001' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 16 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
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
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
EAPOL: disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c07 len=79
AssocReq IE wireless event - hexdump(len=71): 00 0d 73 61 6c 76 61 74 74 6f 72 65 30 30 31 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c 30 26 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 0c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=57
AssocResp IE wireless event - hexdump(len=49): 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c 01 04 82 84 8b 96 03 01 0b dd 16 00 50 f2 01 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:21:29:73:0a:42
Association info event
req_ies - hexdump(len=71): 00 0d 73 61 6c 76 61 74 74 6f 72 65 30 30 31 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c 30 26 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 0c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
resp_ies - hexdump(len=49): 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c 01 04 82 84 8b 96 03 01 0b dd 16 00 50 f2 01 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=40): 30 26 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 0c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
wpa_parse_wpa_ie_rsn: Unsupported management group cipher 0x0
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:21:29:73:0a:42 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED

```

hope you can help me!

---

