---
title: "Please help me debug this wpa_supplicant error"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by pr0fess0r on 2005-12-10
Hi, I'm getting errors with my WiFi card when trying to set it to work with WPA, both with the default prism driver and ndiswrapper. Can anyoen suggest the problem?

prism error:

sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dprism54 -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'prism54'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=9):
     44 49 47 49 54 41 4c 55 53                        DIGITALUS
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='[REMOVED]'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCSIFFLAGS: Timer expired
Could not set interface 'eth1' UP
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:30:b4:00:00:00
wpa_driver_prism54_set_countermeasures - not yet implemented
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
l2_packet_receive - recvfrom: Network is down
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=9):
     RE MO VE DD 54 41 4c 55 53                        REMOVED
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=9):
     RE MO VE DD 54 41 4c 55 53                        REMOVED
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_prism54_set_countermeasures - not yet implemented
No keys have been configured - skip key clearing

ndiswrapper

sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dndiswrapper -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=9):
     XXXXXXXXXXXX                       REMOVED
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='XXXXXXXX'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCSIFFLAGS: Timer expired
Could not set interface 'eth1' UP
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:30:b4:00:00:00
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
l2_packet_receive - recvfrom: Network is down
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=9):
     XXXXXXXXXXXX                       REMOVED
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=9):
     XXXXXXXXXXXX                       REMOVED
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=9):
     XXXXXXXXXXXX                       REMOVED
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=9):
     XXXXXXXXXXXX                       REMOVED
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
No keys have been configured - skip key clearing

Any help would be greatly apreciated

---

