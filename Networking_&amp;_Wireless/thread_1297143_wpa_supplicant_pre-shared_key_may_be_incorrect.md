---
title: "wpa_supplicant pre-shared key may be incorrect"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by heluani on 2009-10-21
Hello list. I am trying to connect to a WPA2 network with wpa_supplicant. My card is a Broadcom with the new hybrid driver wl.ko so I need to use wpa_supplicant with -Dwext. Here is a complete log of 
```
wpa_supplicant -ieth0 -Dwext -c/path/to/myconffile -dd
```
you'll notice the wrong key error towards the end
```
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='root'
ap_scan=1
Line: 8 - start of a new network block
ssid - hexdump_ascii(len=7):
     63 61 6d 70 61 72 69                              campari         
PSK - hexdump(len=32): [REMOVED]
scan_ssid=1 (0x1)
key_mgmt: 0x2
Priority group 0
   id=0 ssid='campari'
Initializing interface (2) 'eth0'
Interface eth0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=19 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1f:f3:ba:45:17
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
ctrl_interface_group=0 (from group name 'root')
Added interface eth0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     63 61 6d 70 61 72 69                              campari         
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
Scan timeout - try to get results
Received 1615 bytes of scan results (7 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:2f:4f:4a:20 ssid='loppy' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1b:63:2c:8b:3c ssid='campari' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:1b:63:2c:8b:3c ssid='campari'
Trying to associate with 00:1b:63:2c:8b:3c (SSID='campari' freq=2452 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:1b:63:2c:8b:3c
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1b:63:2c:8b:3c
No keys have been configured - skip key clearing
Associated with 00:1b:63:2c:8b:3c
WPA: Association event - clear replay counter
WPA: Clear old PTK
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:1b:63:2c:8b:3c
RX EAPOL - hexdump(len=99): 02 03 00 5f 02 00 8a 00 10 00 00 00 00 00 00 00 01 42 69 a6 11 a2 5c 03 27 9e a7 3b 09 8e a7 ae 15 f2 77 ed 38 15 9b 39 84 52 4a 5e f9 56 30 15 e3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=2 type=3 length=95
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 42 69 a6 11 a2 5c 03 27 9e a7 3b 09 8e a7 ae 15 f2 77 ed 38 15 9b 39 84 52 4a 5e f9 56 30 15 e3
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 02 03 00 5f 02 00 8a 00 10 00 00 00 00 00 00 00 01 42 69 a6 11 a2 5c 03 27 9e a7 3b 09 8e a7 ae 15 f2 77 ed 38 15 9b 39 84 52 4a 5e f9 56 30 15 e3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1b:63:2c:8b:3c (ver=2)
RSN: msg 1/4 key data - hexdump(len=0):
WPA: Renewed SNonce - hexdump(len=32): 54 15 bc 68 a2 b3 3b a3 6c d2 13 a7 9c 92 b0 cd 09 08 61 e8 e4 0f d7 2e b7 01 6f 4f f4 59 15 af
WPA: PTK derivation - A1=00:1f:f3:ba:45:17 A2=00:1b:63:2c:8b:3c
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 01 54 15 bc 68 a2 b3 3b a3 6c d2 13 a7 9c 92 b0 cd 09 08 61 e8 e4 0f d7 2e b7 01 6f 4f f4 59 15 af 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b5 b2 c1 a9 c1 55 07 66 41 5f 4d 0a b6 c7 28 0b 00 16 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:00:00:00
[BOLD]WPA: 4-Way Handshake failed - pre-shared key may be incorrect[/BOLD]
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1b:63:2c:8b:3c into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Wireless event: cmd=0x8c02 len=33
WEXT: Custom wireless event: 'Conn Deauth 00 02'
State: DISCONNECTED -> SCANNING
...
```

This is the log when using ap_scan=2 and the full psk=$hexpsk in my wpa_supplicant.conf. Surprisingly enough, if I use wpa_passphrase myssid mypasswd it returns the wrong psk, therefore if in my conf file I put psk="my passphrase" then I noticed in the log file (running with -K) that the wrong psk is sent. 

I must say that the card is working, I can connect to non-wpa points using iwconfig.

Any help will be greatly appreciated.

R.

---

### Post by kevdog on 2009-10-21
Can you post the entire contents of your .conf file rather than bits and pieces?

---

### Post by heluani on 2009-10-21
Tried several combinations, the one for that log is
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
ap_scan=2

network={
        ssid="campari"
        psk=391a3c.....
        scan_ssid=1
        key_mgmt=WPA-PSK
}
```

---

