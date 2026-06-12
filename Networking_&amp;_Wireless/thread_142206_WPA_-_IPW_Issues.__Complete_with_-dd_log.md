---
title: "WPA - IPW Issues.  Complete with -dd log"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by shibasu on 2006-03-10
Followed the Wiki to the T. I have some issues with the IPW drivers as wel, but i'll save those for another time unless someones desperate to help me on that :rolleyes: 

```
 

root@0-0:/etc# wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=9):
     62 65 6c 6b 69 6e 35 34 67                        belkin54g
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='belkin54g'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:12:f0:cc:6a:5b
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
*snip*
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
State: SCANNING -> DISCONNECTED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
*snip*
Scan timeout - try to get results
Received 974 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:11:50:1b:34:63 ssid='belkin54g' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:11:50:1b:34:63 (SSID='belkin54g' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
State: DISCONNECTED -> ASSOCIATING
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=34
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
State: ASSOCIATING -> DISCONNECTED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 3
State: DISCONNECTED -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 976 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:11:50:1b:34:63 ssid='belkin54g' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:11:50:1b:34:63 (SSID='belkin54g' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=34
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 4
State: ASSOCIATING -> DISCONNECTED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
\Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 5
State: DISCONNECTED -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 616 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:11:50:1b:34:63 ssid='belkin54g' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:11:50:1b:34:63 (SSID='belkin54g' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=34
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:11:50:1b:34:63
State: ASSOCIATING -> ASSOCIATED
Associated to a new BSS: BSSID=00:11:50:1b:34:63
No keys have been configured - skip key clearing
Associated with 00:11:50:1b:34:63
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:11:50:1b:34:63
RX EAPOL - hexdump(len=99): *Snip*
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 fe 0e 5a 2d c6 e4 64 fb a2 ea 27 fd 03 a4 a6 ee 01 de d6 60 01 6c 03 3f eb 9d d3 99 6d e5 f0 e9 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:11:50:1b:34:63 (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Renewed SNonce - hexdump(len=32): 4b e4 2b 1c 53 b3 9f 5b 63 9e 95 22 dc 7e fd bc b5 61 03 a0 8c ae 23 86 66 8e 56 a5 4d 42 f1 4b
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 4b e4 2b 1c 53 b3 9f 5b 63 9e 95 22 dc 7e fd bc b5 61 03 a0 8c ae 23 86 66 8e 56 a5 4d 42 f1 4b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6e bc 7c 12 d2 6d a1 55 e1 13 d6 95 ac 5c cf 29 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:11:50:1b:34:63
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 01 fe 0e 5a 2d c6 e4 64 fb a2 ea 27 fd 03 a4 a6 ee 01 de d6 60 01 6c 03 3f eb 9d d3 99 6d e5 f0 e9 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6d cc df 89 1c ce 2f c8 e1 64 a2 cf a0 db 5d c7 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 01 fe 0e 5a 2d c6 e4 64 fb a2 ea 27 fd 03 a4 a6 ee 01 de d6 60 01 6c 03 3f eb 9d d3 99 6d e5 f0 e9 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6d cc df 89 1c ce 2f c8 e1 64 a2 cf a0 db 5d c7 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:11:50:1b:34:63 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 af 02 2e c1 0f 27 20 37 87 fc 96 bf c1 17 b7 3b 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_ipw_set_key: alg=TKIP key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:11:50:1b:34:63
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 02 fe 0e 5a 2d c6 e4 64 fb a2 ea 27 fd 03 a4 a6 ee 01 de d6 60 01 6c 03 3f eb 9d d3 99 6d e5 f0 e6 01 de d6 60 01 6c 03 3f eb 9d d3 99 6d e5 f0 ea 25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 14 be ac c8 89 df 18 e7 df 48 21 44 c5 ff f5 44 00 20 7d d4 f6 2e a1 06 7f 58 2a 8d bc 00 e2 ba 27 ab d5 20 7b 48 05 43 6c 5a 43 f1 92 78 5e 5f 21 15
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 02 fe 0e 5a 2d c6 e4 64 fb a2 ea 27 fd 03 a4 a6 ee 01 de d6 60 01 6c 03 3f eb 9d d3 99 6d e5 f0 e6 01 de d6 60 01 6c 03 3f eb 9d d3 99 6d e5 f0 ea 25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 14 be ac c8 89 df 18 e7 df 48 21 44 c5 ff f5 44 00 20 7d d4 f6 2e a1 06 7f 58 2a 8d bc 00 e2 ba 27 ab d5 20 7b 48 05 43 6c 5a 43 f1 92 78 5e 5f 21 15
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: RX message 1 of Group Key Handshake from 00:11:50:1b:34:63 (ver=1)
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 25 00 00 00 00 00
wpa_driver_ipw_set_key: alg=TKIP key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): *snip*
WPA: Key negotiation completed with 00:11:50:1b:34:63 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:11:50:1b:34:63 completed (auth)
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL: startWhen --> 0

EAPOL: idleWhile --> 0
State: COMPLETED -> DISCONNECTED
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=0
wpa_driver_ipw_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)

```


Just incase it's needed my Ifconfig and iwconfig

```

root@0-0:/home/diux# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:F0:CC:6A:5B
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fecc:6a5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:1 overruns:0 frame:0
          TX packets:12 errors:0 dropped:19 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:7418843 (7.0 MiB)  TX bytes:304200 (297.0 KiB)
          Interrupt:19 Base address:0xa000 Memory:febf9000-febf9fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:903819 (882.6 KiB)  TX bytes:903819 (882.6 KiB)

root@0-0:/home/diux# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"belkin54g"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:0000-0000-0000-0000-0000-0000-0000-0000-0000-0root@0-0:/home/diux# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:F0:CC:6A:5B
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fecc:6a5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:1 overruns:0 frame:0
          TX packets:12 errors:0 dropped:19 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:7418843 (7.0 MiB)  TX bytes:304200 (297.0 KiB)
          Interrupt:19 Base address:0xa000 Memory:febf9000-febf9fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:903819 (882.6 KiB)  TX bytes:903819 (882.6 KiB)


```


Although everything feels online, and my GTK wirless manager tells me im connected, the net, fails. Ping, and all other forms of actual internet connection seem to fail as well. If helpful I could run ethereal while wpa_supplicant is running and post some of the output. 

Thanks for any help you can give me, this has me a good deal :confused: 'd


edit: snip'd for the 30k char limit

---

