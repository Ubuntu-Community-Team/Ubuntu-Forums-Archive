---
title: "WPA supplicant/eduroam cannot connect"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by Wokm4n on 2009-02-02
Hi there,

On my school they use wpa_supplicant for their own wireless network and the provided eduroam.

I can connect with one laptop using these settings:
[https://wiki.aarnet.edu.au/download/attachments/24084544/nm-eduroam-panel.png](https://wiki.aarnet.edu.au/download/attachments/24084544/nm-eduroam-panel.png)
I haven't used a certificate for a year.
Now I got this new laptop (HP Mininote) and I cannot connect to the wireless network. Maybe this is something about the general wireless support for this device since I also can't connect to hidden wireless networks.

Here's output from deamon.log:
[http://pastebin.com/m65a1c56e](http://pastebin.com/m65a1c56e)

Is there any info I can provide?
I hope I can get this to work since I also cannot connect to eth since they use cisco clean access agent! :(

---

### Post by vpablos on 2009-02-04
Hi.

I've a problem related to this. It is because wpa_supplicant does not accept the university certificate.

Here is the problem:

SSL: SSL_connect:SSLv3 read server hello A
TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=PT/ST=Lisbon/L=Lisbon/O=Universidade Nova de Lisboa/OU=Reitoria/CN=Universidade Nova de Lisboa/emailAddress=informatica@unl.pt'
SSL: (where=0x4008 ret=0x230)
SSL: SSL3 alert: write (local SSL3 detected an error):fatal:unknown CA
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read server certificate B
OpenSSL: tls_connection_handshake - SSL_connect error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
SSL: 7 bytes pending from ssl_out
SSL: Failed - tls_out available to report error
SSL: 7 bytes left to be sent out (of total 7 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL


And here is the complete log:

Initializing interface 'wlan0' conf '/var/lib/wicd/configurations/0011216c4290' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/var/lib/wicd/configurations/0011216c4290' -> '/var/lib/wicd/configurations/0011216c4290'
Reading configuration file '/var/lib/wicd/configurations/0011216c4290'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=1
fast_reauth=0
Priority group 0
   id=0 ssid='eduroam'
Initializing interface (2) 'wlan0'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:de:a8:42:a5
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1955 bytes of scan results (5 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:11:21:6c:42:90 ssid='eduroam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - key mgmt mismatch
1: 00:12:da:9e:31:50 ssid='eduroam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - key mgmt mismatch
2: 00:11:21:6c:42:91 ssid='eduroam-guest' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:12:da:9e:31:51 ssid='eduroam-guest' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
4: 00:12:da:9e:30:31 ssid='eduroam-guest' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:11:21:6c:42:90 ssid='eduroam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:11:21:6c:42:90 ssid='eduroam'
Trying to associate with 00:11:21:6c:42:90 (SSID='eduroam' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c02 len=187
Association info event
req_ies - hexdump(len=34): 00 07 65 64 75 72 6f 61 6d 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 07 00 50 f2 02 00 01 00
resp_ies - hexdump(len=42): 01 08 82 84 8b 96 0c 12 18 24 32 04 30 48 60 6c dd 18 00 50 f2 02 01 01 88 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
WPA: clearing own WPA/RSN IE
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:11:21:6c:42:90
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:11:21:6c:42:90
No keys have been configured - skip key clearing
Associated with 00:11:21:6c:42:90
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:11:21:6c:42:90
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=1 method=1 vendor=0 vendorMethod=0
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=46):
     00 6e 65 74 77 6f 72 6b 69 64 3d 65 64 75 72 6f   _networkid=eduro
     61 6d 2c 6e 61 73 69 64 3d 41 70 50 32 34 2e 49   am,nasid=ApP24.I
     49 2e 66 63 74 2c 70 6f 72 74 69 64 3d 30         I.fct,portid=0  
EAP: using anonymous identity - hexdump_ascii(len=20):
     76 2e 63 65 72 75 65 6c 6f 40 66 63 74 2e 75 6e   [email]v.ceruelo@fct.un[/email]
     6c 2e 70 74                                       l.pt            
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: authWhile --> 0
EAPOL: SUPP_BE entering state TIMEOUT
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:11:21:6c:42:90 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such file or directory
Driver did not support SIOCSIWENCODEEXT
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 394 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:11:21:6c:42:90 ssid='eduroam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - key mgmt mismatch
Try to find non-WPA AP
0: 00:11:21:6c:42:90 ssid='eduroam' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:11:21:6c:42:90 ssid='eduroam'
Trying to associate with 00:11:21:6c:42:90 (SSID='eduroam' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c02 len=187
Association info event
req_ies - hexdump(len=34): 00 07 65 64 75 72 6f 61 6d 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 07 00 50 f2 02 00 01 00
resp_ies - hexdump(len=42): 01 08 82 84 8b 96 0c 12 18 24 32 04 30 48 60 6c dd 18 00 50 f2 02 01 01 88 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
WPA: clearing own WPA/RSN IE
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:11:21:6c:42:90
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:11:21:6c:42:90
No keys have been configured - skip key clearing
Associated with 00:11:21:6c:42:90
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:11:21:6c:42:90
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=1 method=1 vendor=0 vendorMethod=0
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=46):
     00 6e 65 74 77 6f 72 6b 69 64 3d 65 64 75 72 6f   _networkid=eduro
     61 6d 2c 6e 61 73 69 64 3d 41 70 50 32 34 2e 49   am,nasid=ApP24.I
     49 2e 66 63 74 2c 70 6f 72 74 69 64 3d 30         I.fct,portid=0  
EAP: using anonymous identity - hexdump_ascii(len=20):
     76 2e 63 65 72 75 65 6c 6f 40 66 63 74 2e 75 6e   [email]v.ceruelo@fct.un[/email]
     6c 2e 70 74                                       l.pt            
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:11:21:6c:42:90
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=2 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state GET_METHOD
EAP: configuration does not allow: vendor 0 method 25
EAP: vendor 0 method 25 not allowed
EAP: Building EAP-Nak (requested type 25 vendor=0 method=0 not allowed)
EAP: allowed methods - hexdump(len=1): 15
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:11:21:6c:42:90
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=3 method=21 vendor=0 vendorMethod=0
EAP: EAP entering state GET_METHOD
EAP: Initialize selected EAP method: vendor 0 method 21 (TTLS)
EAP-TTLS: Phase2 type: PAP
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
EAP: EAP entering state METHOD
SSL: Received packet(len=6) - Flags 0x20
EAP-TTLS: Start (server ver=0, own ver=0)
TLS: Trusted root certificate(s) loaded
EAP-TTLS: Start
SSL: (where=0x10 ret=0x1)
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:before/connect initialization
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client hello A
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read server hello A
SSL: SSL_connect - want more data
SSL: 93 bytes pending from ssl_out
SSL: 93 bytes left to be sent out (of total 93 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:11:21:6c:42:90
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=4 method=21 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1024) - Flags 0xc0
SSL: TLS Message Length: 3611
SSL: Need 2597 bytes more input data
SSL: Building ACK (type=21 id=4 ver=0)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:11:21:6c:42:90
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=5 method=21 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1024) - Flags 0xc0
SSL: TLS Message Length: 3611
SSL: Need 1583 bytes more input data
SSL: Building ACK (type=21 id=5 ver=0)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:11:21:6c:42:90
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=6 method=21 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1024) - Flags 0xc0
SSL: TLS Message Length: 3611
SSL: Need 569 bytes more input data
SSL: Building ACK (type=21 id=6 ver=0)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:11:21:6c:42:90
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=7 method=21 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=579) - Flags 0x80
SSL: TLS Message Length: 3611
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server hello A
TLS: Certificate verification failed, error 19 (self signed certificate in certificate chain) depth 1 for '/C=PT/ST=Lisbon/L=Lisbon/O=Universidade Nova de Lisboa/OU=Reitoria/CN=Universidade Nova de Lisboa/emailAddress=informatica@unl.pt'
SSL: (where=0x4008 ret=0x230)
SSL: SSL3 alert: write (local SSL3 detected an error):fatal:unknown CA
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read server certificate B
OpenSSL: tls_connection_handshake - SSL_connect error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
SSL: 7 bytes pending from ssl_out
SSL: Failed - tls_out available to report error
SSL: 7 bytes left to be sent out (of total 7 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:11:21:6c:42:90
EAPOL: SUPP_BE entering state RECEIVE
^CCTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
EAP: deinitialize previously used EAP method (21, TTLS) at EAP deinit
ENGINE: engine deinit
Removed BSSID 00:11:21:6c:42:90 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout


Obviously dmesg says "deauthenticating by local choice"

[ 1234.641727] wlan0: direct probe to AP 00:11:21:6c:42:90 try 1
[ 1234.646702] wlan0 direct probe responded
[ 1234.646714] wlan0: authenticate with AP 00:11:21:6c:42:90
[ 1234.652706] wlan0: authenticated
[ 1234.652718] wlan0: associate with AP 00:11:21:6c:42:90
[ 1234.654568] wlan0: RX ReassocResp from 00:11:21:6c:42:90 (capab=0x431 status=0 aid=38)
[ 1234.654575] wlan0: associated
[ 1236.605455] wlan0: deauthenticating by local choice (reason=3)

How can I fix this?

Regards, 

Victor

---

