---
title: "Wusb11 V4"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by sciurus on 2006-06-29
Is there a native linux driver for the WUSB11v4? I know previous versions were supported by atmel or prism2 drivers, but this revision uses the ALi M4301A chip.

---

### Post by sciurus on 2006-06-29
I successfully installed my device with ndiswrapper and can connect to wirelss networks using iwconfig. I tried NetworkManager for ease of use, but it will never connect to any access points.

[PHP]    [1151639578.884810] nm_device_802_11_wireless_ge t_activation_ap (): Forcing AP 'default'
NetworkManager: <information>   User Switch: /org/freedesktop/NetworkManager/Dev ices/wlan0 / default
NetworkManager: <information>   Deactivating device wlan0.
NetworkManager: <information>   Device wlan0 activation scheduled...
NetworkManager: <information>   Deactivating device eth1.
NetworkManager: <information>   Activation (wlan0) started...
NetworkManager: <information>   Activation (wlan0) Stage 1 of 5 (Device Prepare)  scheduled...
NetworkManager: <information>   Activation (wlan0) Stage 1 of 5 (Device Prepare)  started...
NetworkManager: <information>   Activation (wlan0) Stage 2 of 5 (Device Configur e) scheduled...
NetworkManager: <information>   Activation (wlan0) Stage 1 of 5 (Device Prepare)  complete.
NetworkManager: <information>   Activation (wlan0) Stage 2 of 5 (Device Configur e) starting...
NetworkManager: <information>   Activation (wlan0/wireless): access point 'defau lt' is unencrypted, no key needed.
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD wlan0      n diswrapper      /var/run/wpa_supplicant '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 1'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ADD_NETWORK'
NetworkManager: <information>   SUP: response was '0'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 ssid 6465666 1756c74'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 key_mgmt NON E'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   Activation (wlan0) Stage 2 of 5 (Device Configur e) complete.
NetworkManager: <information>   wpa_supplicant(6916): Global control interface ' /var/run/wpa_supplicant-global'
NetworkManager: <information>   wpa_supplicant(6916): RX global ctrl_iface - hex dump_ascii(len=57):
NetworkManager: <information>   wpa_supplicant(6916):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 77 6c   INTERFACE_ADD wl
NetworkManager: <information>   wpa_supplicant(6916):      61 6e 30 09 09 6e 64 69 73 77 72 61 70 70 65 72   an0__ndiswrapper
NetworkManager: <information>   wpa_supplicant(6916):      09 2f 76 61 72 2f 72 75 6e 2f 77 70 61 5f 73 75   _/var/run/wpa_su
NetworkManager: <information>   wpa_supplicant(6916):      70 70 6c 69 63 61 6e 74 09                        pplicant_
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE GLOBAL INTERFAC E_ADD 'wlan0            ndiswrapper     /var/run/wpa_supplicant '
NetworkManager: <information>   wpa_supplicant(6916): Initializing interface 'wl an0' conf 'N/A' driver 'ndiswrapper' ctrl_interface '/var/run/wpa_supplicant'
NetworkManager: <information>   wpa_supplicant(6916): Initializing interface (2)  'wlan0'
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: SUPP_PAE entering s tate DISCONNECTED
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: KEY_RX entering sta te NO_KEY_RECEIVE
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: SUPP_BE entering st ate INITIALIZE
NetworkManager: <information>   wpa_supplicant(6916): EAP: EAP entering state DI SABLED
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notificati on - portEnabled=0
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notificati on - portValid=0
NetworkManager: <information>   wpa_supplicant(6916): SIOCGIWRANGE: WE(compiled) =19 WE(source)=18 enc_capa=0x5
NetworkManager: <information>   wpa_supplicant(6916):   capabilities: key_mgmt 0 x5 enc 0x7
NetworkManager: <information>   wpa_supplicant(6916): Own MAC address: 00:12:17: 60:2c:13
NetworkManager: <information>   wpa_supplicant(6916): idx=0 set_tx=0 seq_len=0 k ey_len=0
NetworkManager: <information>   wpa_supplicant(6916): wpa_driver_wext_set_key: a lg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(6916): wpa_driver_wext_set_key: a lg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(6916): wpa_driver_wext_set_key: a lg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(6916): Setting scan request: 0 se c 100000 usec
NetworkManager: <information>   wpa_supplicant(6916): Added interface wlan0
NetworkManager: <information>   wpa_supplicant(6916): Wireless event: cmd=0x8b06  len=8
NetworkManager: <information>   wpa_supplicant(6916): RX ctrl_iface - hexdump_as cii(len=9):
NetworkManager: <information>   wpa_supplicant(6916):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1
NetworkManager: <information>   wpa_supplicant(6916): RX ctrl_iface - hexdump_as cii(len=11):
NetworkManager: <information>   wpa_supplicant(6916):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE: ADD_NETWORK
NetworkManager: <information>   wpa_supplicant(6916): RX ctrl_iface - hexdump_as cii(len=33):
NetworkManager: <information>   wpa_supplicant(6916):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss
NetworkManager: <information>   wpa_supplicant(6916):      69 64 20 36 34 36 35 36 36 36 31 37 35 36 63 37   id 64656661756c7
NetworkManager: <information>   wpa_supplicant(6916):      34                              4
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE: SET_NETWORK id =0 name='ssid' value='64656661756c74'
NetworkManager: <information>   wpa_supplicant(6916): ssid - hexdump_ascii(len=7 ):
NetworkManager: <information>   wpa_supplicant(6916):      64 65 66 61 75 6c 74                              default
NetworkManager: <information>   wpa_supplicant(6916): xdump_ascii(len=27):
NetworkManager: <information>   wpa_supplicant(6916):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke
NetworkManager: <information>   wpa_supplicant(6916):      79 5f 6d 67 6d 74 20 4e 4f 4e 45                  y_mgmt NONE
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE: SET_NETWORK id =0 name='key_mgmt' value='NONE'
NetworkManager: <information>   wpa_supplicant(6916): key_mgmt: 0x4
NetworkManager: <information>   wpa_supplicant(6916): RX ctrl_iface - hexdump_as cii(len=16):
NetworkManager: <information>   wpa_supplicant(6916):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE: ENABLE_NETWORK  id=0
NetworkManager: <information>   wpa_supplicant(6916): Setting scan request: 0 se c 0 usec
NetworkManager: <information>   wpa_supplicant(6916): State: DISCONNECTED -> SCA NNING
NetworkManager: <information>   wpa_supplicant(6916): Starting AP scan (broadcas t SSID)
NetworkManager: <information>   wpa_supplicant(6916): RX ctrl_iface - hexdump_as cii(len=6):
NetworkManager: <information>   wpa_supplicant(6916):      41 54 54 41 43 48                              ATTACH
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE monitor attache d - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61  67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 38 34 33 2d 31 00 30 00
NetworkManager: <information>   wpa_supplicant(6916): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(6916): Received 1352 bytes of sca n results (8 BSSes)
NetworkManager: <information>   wpa_supplicant(6916): Scan results: 8
NetworkManager: <information>   wpa_supplicant(6916): Selecting BSS from priorit y group 0
NetworkManager: <information>   wpa_supplicant(6916): 0: 00:0d:93:eb:f3:ad ssid= 'la ponderosa' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - SSID mismatch
NetworkManager: <information>   wpa_supplicant(6916): ='prateekgoel' wpa_ie_len= 0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 2: 00:09:5b:11:7c:64 ssid= 'Matt' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 3: 00:30:bd:c9:c4:14 ssid= 'PBwireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 4: 00:30:bd:ca:09:3c ssid= '' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 5: 00:11:50:40:4c:f5 ssid= '1538E' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 6: 00:01:95:6a:31:1f ssid= 'default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 7: 00:0e:2e:6d:d8:05 ssid= 'Circlophile' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916):    selected non-WPA AP 00: 01:95:6a:31:1f ssid='default'
NetworkManager: <information>   wpa_supplicant(6916): Trying to associate with 0 0:01:95:6a:31:1f (SSID='default' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 38 34 33 2d 31 00 30 00
NetworkManager: <information>   wpa_supplicant(6916): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): : 0x1
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(6916): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(6916): Setting authentication timeout: 10 sec 0 usec
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(6916): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 38 34 33 2d 31 00 30 00
NetworkManager: <information>   wpa_supplicant(6916): Added BSSID 00:00:00:00:00:00 into blacklist
NetworkManager: <information>   wpa_supplicant(6916): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(6916): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(6916): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(6916): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(6916): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(6916): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(6916): Received 1672 bytes of scan results (10 BSSes)
NetworkManager: <information>   wpa_supplicant(6916): Scan results: 10
NetworkManager: <information>   wpa_supplicant(6916): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(6916): 0: 00:0d:93:eb:f3:ad ssid='la ponderosa' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):  - SSID mismatch
NetworkManager: <information>   wpa_supplicant(6916): 1: 00:90:4c:7e:00:64 ssid='prateekgoel' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 2: 00:12:88:67:df:a1 ssid='2WIRE948' wpa_ie_len=0 rsn_ie_len=0 caps=0x11NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 3: 00:0d:3a:2a:64:7e ssid='waynetwork' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 4: 00:09:5b:11:7c:64 ssid='Matt' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 5: 00:30:bd:c9:c4:14 ssid='PBwireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 6: 00:30:bd:ca:09:3c ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 7: 00:0f:3d:50:52:64 ssid='mrigesh' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 8: 00:11:50:40:4c:f5 ssid='1538E' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 9: 00:01:95:6a:31:1f ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916):    selected non-WPA AP 00:01:95:6a:31:1f ssid='default'
NetworkManager: <information>   wpa_supplicant(6916): Trying to associate with 00:01:95:6a:31:1f (SSID='default' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(6916): tor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 38 34 33 2d 31 00 30 00
NetworkManager: <information>   wpa_supplicant(6916): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(6916): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(6916): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(6916): Setting authentication timeout: 10 sec 0 usec
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(6916): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(6916): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 38 34 33 2d 31 00 30 00
NetworkManager: <information>   wpa_supplicant(6916): BSSID 00:00:00:00:00:00 blacklist count incremented to 2
NetworkManager: <information>   wpa_supplicant(6916): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(6916): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(6916): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(6916): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(6916): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(6916): ng AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(6916): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(6916): Received 1836 bytes of scan results (11 BSSes)
NetworkManager: <information>   wpa_supplicant(6916): Scan results: 11
NetworkManager: <information>   wpa_supplicant(6916): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(6916): 0: 00:0d:93:eb:f3:ad ssid='la ponderosa' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - SSID mismatch
NetworkManager: <information>   wpa_supplicant(6916): 1: 00:90:4c:7e:00:64 ssid='prateekgoel' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 2: 00:30:bd:ca:09:3c ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 3: 00:0d:3a:2a:64:7e ssid='waynetwork' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 4: 00:12:88:67:df:a1 ssid='2WIRE948' wpa_ie_len=0 rsn_ie_len=0 caps=0x11NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 5: 00:09:5b:11:7c:64 ssid='Matt' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 6: 00:30:bd:c9:c4:14 ssid='PBwireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 7: 00:0f:3d:50:52:64 ssid='mrigesh' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
NetworkManager: <information>   wpa_supplicant(6916):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(6916): 8: 00:11:50:40:4c:f5 ssid='1538E' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
<information>     Activation (wlan0/wireless): association took too long (>60s), failing activation.
NetworkManager: <information>   Activation (wlan0) failure scheduled...
NetworkManager: <information>   Activation (wlan0) failed for access point (default)
NetworkManager: <information>   Activation (wlan0) failed.
NetworkManager: <information>   Deactivating device wlan0.
sendmsg(CTRL_IFACE monitor): No such file or directory
ioctl[SIOCSIWAP]: Operation not supported
NetworkManager: <information>   SWITCH: no current connection, found better connection 'eth1'.
NetworkManager: <information>   Will activate connection 'eth1'.
[/PHP]

---

