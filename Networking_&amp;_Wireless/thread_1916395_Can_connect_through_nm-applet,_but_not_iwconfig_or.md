---
title: "Can connect through nm-applet, but not iwconfig or cnetworkmanager."
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by srilyk on 2012-01-27
Hi,

I've got a strange problem with my wifi. I'm running Ubuntu 10.10 on an IBM ThinkPad R60. I can connect to the wifi fine using nm-applet - WEP, WPA, whatever I have no problems.

However, I would prefer to not have to start X as my system is a bit weak on the specs, so I've removed the login manager and it starts up in text mode (with some slight weirdness but that's for another post), and everything works fine -but- I cannot connect using anything but nm-applet.

I've tried wpa_supplicant, iwconfig, and cnetworkmanager all with no success.

cnetworkmanager tells me:

Entering mainloop
(22:04:50) State: CONNECTING
(22:04:50) State: DISCONNECTED
Can only connect through nm-applet

If I do iwconfig I do:

sudo iwconfig wlan0 mode managed key s:notmyrealpw essid notmyrealessideither

Then 

sudo dhclient

Which fails to get a DHCP offer.

For wpa_supplicant, I get the most bizarre behavior - it continually connects, then disconnects from the AP, regardless of encryption type (WPA, WEP, or none). Here is some of the output from wpa_supplicant:

```
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
RX ctrl_iface - hexdump_ascii(len=22):
     47 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 64 69   GET_NETWORK 0 di
     73 61 62 6c 65 64                                 sabled          
CTRL_IFACE: GET_NETWORK id=0 name='disabled'
RX ctrl_iface - hexdump_ascii(len=13):
     4c 49 53 54 5f 4e 45 54 57 4f 52 4b 53            LIST_NETWORKS   
RX ctrl_iface - hexdump_ascii(len=22):
     47 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 64 69   GET_NETWORK 0 di
     73 61 62 6c 65 64                                 sabled          
CTRL_IFACE: GET_NETWORK id=0 name='disabled'
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 959 bytes of scan results (3 BSSes)
New scan results available
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:95:71:df:09 ssid='2WIRE916' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   skip - SSID mismatch
1: 00:22:f0:0d:d0:c0 ssid='thingummy' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1a:70:e3:9a:98 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:95:71:df:09 ssid='2WIRE916' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   skip - SSID mismatch
1: 00:22:f0:0d:d0:c0 ssid='thingummy' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   selected non-WPA AP 00:22:f0:0d:d0:c0 ssid='thingummy'
Trying to associate with 00:22:f0:0d:d0:c0 (SSID='thingummy' freq=2412 MHz)
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=1 seq_len=0 key_len=13
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=20
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=61
AssocResp IE wireless event - hexdump(len=53): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 09 00 10 18 02 03 f0 00 00 00 dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:22:f0:0d:d0:c0
Association info event
resp_ies - hexdump(len=53): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 09 00 10 18 02 03 f0 00 00 00 dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (reauth) [id=1 id_str=]
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
BSSID 00:22:f0:0d:d0:c0 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
RX ctrl_iface - hexdump_ascii(len=22):
     47 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 64 69   GET_NETWORK 0 di
     73 61 62 6c 65 64                                 sabled          
CTRL_IFACE: GET_NETWORK id=0 name='disabled'
RX ctrl_iface - hexdump_ascii(len=13):
     4c 49 53 54 5f 4e 45 54 57 4f 52 4b 53            LIST_NETWORKS   
RX ctrl_iface - hexdump_ascii(len=22):
     47 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 64 69   GET_NETWORK 0 di
     73 61 62 6c 65 64                                 sabled          
CTRL_IFACE: GET_NETWORK id=0 name='disabled'
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 959 bytes of scan results (3 BSSes)
New scan results available
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:95:71:df:09 ssid='2WIRE916' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   skip - SSID mismatch
1: 00:22:f0:0d:d0:c0 ssid='thingummy' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:1a:70:e3:9a:98 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:95:71:df:09 ssid='2WIRE916' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   skip - SSID mismatch
1: 00:22:f0:0d:d0:c0 ssid='thingummy' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:1a:70:e3:9a:98 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:22:f0:0d:d0:c0 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:95:71:df:09 ssid='2WIRE916' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   skip - SSID mismatch
1: 00:22:f0:0d:d0:c0 ssid='thingummy' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1a:70:e3:9a:98 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:95:71:df:09 ssid='2WIRE916' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   skip - SSID mismatch
1: 00:22:f0:0d:d0:c0 ssid='thingummy' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   selected non-WPA AP 00:22:f0:0d:d0:c0 ssid='thingummy'
Trying to associate with 00:22:f0:0d:d0:c0 (SSID='thingummy' freq=2412 MHz)
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=1 seq_len=0 key_len=13
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=20
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=61
AssocResp IE wireless event - hexdump(len=53): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 09 00 10 18 02 03 f0 00 00 00 dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:22:f0:0d:d0:c0
Association info event
resp_ies - hexdump(len=53): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 09 00 10 18 02 03 f0 00 00 00 dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (reauth) [id=1 id_str=]
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:22:f0:0d:d0:c0 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL_IFACE monitor send - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 38 32 30 2d 32 00
State: COMPLETED -> DISCONNECTED
```

Any clue as to why I can't connect using anything besides nm-applet? 

Oh, also:

$ lspci | grep Network
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Thanks for any advice!

---

