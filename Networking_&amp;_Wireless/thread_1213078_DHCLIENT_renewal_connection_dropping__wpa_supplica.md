---
title: "DHCLIENT renewal connection dropping / wpa_supplicant suspend issue"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by steveedwards01 on 2009-07-14
Hello everyone,

Yesterday I setup Ubuntu wifi connection using WPA PSK to a Thompson TG 585 wifi / dsl router.

I'm running Hardy Heron so to obtain support for WPA encrypted link I downloaded wpa_supplicant, upgraded Network Manager and dhclient (to v3.0.6) via package mgr.

After setting it up I experienced a very annoying problem with connection dropping ~30seconds after getting online.  Re-running dhclient restores connection which then drops again after short interval.

First thing i notice is wpa_supplicant takes ages (~1minute) to make connection and reports lots of disconnects when run in non debug mode -

root@user-PC:~# wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w
sudo: unable to resolve host user-PC
Trying to associate with 00:24:17:1f:43:95 (SSID='BeBox' freq=2412 MHz)
Associated with 00:24:17:1f:43:95
Authentication with 00:24:17:1f:43:95 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:24:17:1f:43:95 (SSID='BeBox' freq=2412 MHz)
Associated with 00:24:17:1f:43:95
Authentication with 00:24:17:1f:43:95 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:24:17:1f:43:95 (SSID='BeBox' freq=2412 MHz)
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Associated with 00:24:17:1f:43:95
Authentication with 00:24:17:1f:43:95 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:24:17:1f:43:95 (SSID='BeBox' freq=2412 MHz)
Associated with 00:24:17:1f:43:95
Authentication with 00:24:17:1f:43:95 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:24:17:1f:43:95 (SSID='BeBox' freq=2412 MHz)
Associated with 00:24:17:1f:43:95
Authentication with 00:24:17:1f:43:95 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:24:17:1f:43:95 (SSID='BeBox' freq=2412 MHz)
Associated with 00:24:17:1f:43:95
WPA: Key negotiation completed with 00:24:17:1f:43:95 [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:24:17:1f:43:95 completed (auth) [id=0 id_str=]

iwevent log similarly reports disconnect events (New Access Point/Cell address:Not-Associated) as follows -

root@user-PC:~# iwevent
Waiting for Wireless Events from interfaces...
13:46:51.955898   wlan0    Set Mode:Managed
13:46:52.163024   wlan0    Set Mode:Managed
13:46:52.163052   wlan0    Set Frequency:2.412 GHz (Channel 1)
13:46:52.164150   wlan0    Set ESSID:"BeBox"
13:46:52.617601   wlan0    Association Request  IEs:00054265426F78010882848B962430486C210208122402010E32040C121860DD09001018020010000000DD180050F20101000050F20201000050F2040100005
13:46:52.617679   wlan0    Association Response IEs:010882848B962430486C32040C121860DD060010180200F0
13:46:52.617703   wlan0    New Access Point/Cell address:00:24:17:1F:43:95
13:47:02.628221   wlan0    New Access Point/Cell address:Not-Associated
13:47:05.630131   wlan0    Set Mode:Managed
13:47:05.630166   wlan0    Set Frequency:2.412 GHz (Channel 1)
13:47:05.630196   wlan0    Set ESSID:"BeBox"
13:47:06.082892   wlan0    Association Request IEs:00054265426F78010882848B962430486C210208122402010E32040C121860DD09001018020010000000DD180050F20101000050F20201000050F2040100005
13:47:06.082959   wlan0    Association Response IEs:010882848B962430486C32040C121860DD060010180200F0
13:47:06.082983   wlan0    New Access Point/Cell address:00:24:17:1F:43:95
13:47:16.093806   wlan0    New Access Point/Cell address:Not-Associated
13:47:19.095164   wlan0    Set Mode:Managed
13:47:19.095199   wlan0    Set Frequency:2.412 GHz (Channel 1)
13:47:19.095227   wlan0    Set ESSID:"BeBox"
13:47:19.546002   wlan0    Association Request IEs:00054265426F78010882848B962430486C210208122402010E32040C121860DD09001018020010000000DD180050F20101000050F20201000050F2040100005
13:47:19.546077   wlan0    Association Response IEs:010882848B962430486C32040C121860DD060010180200F0
13:47:19.546102   wlan0    New Access Point/Cell address:00:24:17:1F:43:95
13:47:30.562841   wlan0    New Access Point/Cell address:Not-Associated
13:47:33.563139   wlan0    Set Mode:Managed
13:47:33.563171   wlan0    Set Frequency:2.412 GHz (Channel 1)
13:47:33.563199   wlan0    Set ESSID:"BeBox"
13:47:34.013973   wlan0    Association Request 
....cut

Running wpa_supplicant in debug mode (-dd) a connection is made very promptly  (see log below in appendix 1).  Then I run dhclient to obtain IP address via DHCP, connection is ok and I can ping / browse web.

But after ~30 seconds connection appears to drop (browsing / ping fails).  Running dhclient via shell again restores connection but after 30secs it drops again.  Very annoying!

First I run several test - using wireless interface with WEP then using wired ethernet cable connection - exactly same issue: a short interval after connecting successfully internet is "down".  So problem looks like dhclient! 

So i use wireshark to see what packets are going across the wifi link (see appendix 2) and I see that despite appearing to be offline (no ping response / unable to browse) once connection drops at network level TCP / ICMP  packets are still being sent / revieved from remote hosts - and yet in userspace link appears down.  

Problem seems to occur with DHCP renewal request / ack

Initial DHCP request, sucessful response - IP assigned, link ok.

     18 25.537198   0.0.0.0               255.255.255.255       DHCP     DHCP Request  - Transaction ID 0x374fb673
     21 26.553279   192.168.1.254         192.168.1.77          DHCP     DHCP ACK      - Transaction ID 0x374fb673


     59 71.672729   192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
     62 71.955942   192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - 
Transaction ID 0x5d155a05

At this point connection appears down beyond this point and it seems dhclient is continually polling router with lease request.


     63 77.536127   192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
     64 77.541404   192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - Transaction ID 0x5d155a05
     65 84.536124   192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
     66 84.541455   192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - Transaction ID 0x5d155a05
     99 104.536141  192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
    100 104.541755  192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - Transaction ID 0x5d155a05


To prove issue is dhclient I setup link with static IP address :

root@user-PC:~# cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.77
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.254 

Works fine!  Connection doesn't drop at all.  Looks to me like bug in dhclient when issuing renewal requests.  

Second (less critical problem )- is that after connecting OK using wpa_supplicant / static IP after putting laptop into suspend wifi link is down and does not come back up.  Have to /etc/init.d/networking stop/start, kill wpa_supplicant restart connection.


Hope this is useful to developers or others who may experience similar problems.

Keep up the good work ubuntu team, great distro !

Steve



Appendix 1

root@user-PC:~# sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w -dd
sudo: unable to resolve host user-PC
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=5):
     42 65 42 6f 78                                    BeBox           
proto: 0x1
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='BeBox'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:16:44:bf:dd:4a
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1034 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:24:17:1f:43:95 ssid='BeBox' wpa_ie_len=30 rsn_ie_len=26 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:24:17:1f:43:95 ssid='BeBox'
Try to find non-WPA AP
Trying to associate with 00:24:17:1f:43:95 (SSID='BeBox' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 00 00
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
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=13
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=84
AssocReq IE wireless event - hexdump(len=76): 00 05 42 65 42 6f 78 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=32
AssocResp IE wireless event - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 00 f0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:24:17:1f:43:95
Association info event
req_ies - hexdump(len=76): 00 05 42 65 42 6f 78 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
resp_ies - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 00 f0
WPA: set own WPA/RSN IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:24:17:1f:43:95
No keys have been configured - skip key clearing
Associated with 00:24:17:1f:43:95
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:24:17:1f:43:95
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 00 01 a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3d
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 00 01 a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:24:17:1f:43:95 (ver=2)
WPA: Renewed SNonce - hexdump(len=32): c1 90 b6 96 b2 d4 30 f1 67 83 f1 b4 10 90 6f 58 94 7f 3a cf a6 54 9d 0f 64 39 9b f4 64 af cc d5
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 0a 00 10 00 00 00 00 00 00 00 01 c1 90 b6 96 b2 d4 30 f1 67 83 f1 b4 10 90 6f 58 94 7f 3a cf a6 54 9d 0f 64 39 9b f4 64 af cc d5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 41 49 70 f9 23 5f 21 ef 42 88 43 6d ca 26 e8 94 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
RX EAPOL from 00:24:17:1f:43:95
RX EAPOL - hexdump(len=129): 01 03 00 7d fe 01 ca 00 10 00 00 00 00 00 00 00 02 a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b8 11 75 d8 d6 29 b3 43 6b 48 a8 15 12 67 b9 ed 00 1e dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 00 00
IEEE 802.1X RX: version=1 type=3 length=125
  EAPOL-Key type=254
  key_info 0x1ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=16 key_data_length=30
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3d
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): b8 11 75 d8 d6 29 b3 43 6b 48 a8 15 12 67 b9 ed
WPA: RX EAPOL-Key - hexdump(len=129): 01 03 00 7d fe 01 ca 00 10 00 00 00 00 00 00 00 02 a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b8 11 75 d8 d6 29 b3 43 6b 48 a8 15 12 67 b9 ed 00 1e dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:24:17:1f:43:95 (ver=2)
WPA: IE KeyData - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 0a 00 10 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 75 26 05 e7 c5 ae 70 87 70 f2 94 4b d2 82 c1 81 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:24:17:1f:43:95
RX EAPOL - hexdump(len=139): 01 03 00 87 fe 03 92 00 20 00 00 00 00 00 00 00 03 a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 23 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 11 45 04 bd 7b c8 d5 c1 7a 82 54 48 7e 80 89 85 00 28 df 32 c8 0f 3d 2b 4b ef 00 a4 29 85 cc 3f 00 97 a5 2e 3f 06 04 b3 3c e6 d6 11 81 f1 4c 01 ca 5b 5f 66 93 d2 7e 44 22 ec
IEEE 802.1X RX: version=1 type=3 length=135
  EAPOL-Key type=254
  key_info 0x392 (ver=2 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=40
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 23
  key_iv - hexdump(len=16): 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3e
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 11 45 04 bd 7b c8 d5 c1 7a 82 54 48 7e 80 89 85
WPA: RX EAPOL-Key - hexdump(len=139): 01 03 00 87 fe 03 92 00 20 00 00 00 00 00 00 00 03 a5 71 4a 1b be 4f 6a 44 57 78 06 19 08 c4 67 50 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 23 9b fb 64 42 ee 77 c9 36 39 65 0f e7 f0 c1 51 3e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 11 45 04 bd 7b c8 d5 c1 7a 82 54 48 7e 80 89 85 00 28 df 32 c8 0f 3d 2b 4b ef 00 a4 29 85 cc 3f 00 97 a5 2e 3f 06 04 b3 3c e6 d6 11 81 f1 4c 01 ca 5b 5f 66 93 d2 7e 44 22 ec
WPA: RX message 1 of Group Key Handshake from 00:24:17:1f:43:95 (ver=2)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 12 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c3 1c e1 9c 4a e3 5e 1b 93 b3 9c 41 5f 45 08 05 00 00
WPA: Key negotiation completed with 00:24:17:1f:43:95 [PTK=CCMP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:24:17:1f:43:95 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0

Appendix 2 wireshark dump
No.     Time        Source                Destination           Protocol Info
      1 0.000000    ::                    ff02::16              ICMPv6   Multicast Listener Report Message v2
      2 0.340046    ::                    ff02::1:ffbf:dd4a     ICMPv6   Neighbor solicitation
      3 1.000383    00:24:17:1f:43:95     Lite-OnT_bf:dd:4a     EAPOL    Key
      4 1.002816    Lite-OnT_bf:dd:4a     00:24:17:1f:43:95     EAPOL    Key
      5 1.006974    00:24:17:1f:43:95     Lite-OnT_bf:dd:4a     EAPOL    Key
      6 1.007386    Lite-OnT_bf:dd:4a     00:24:17:1f:43:95     EAPOL    Key
      7 1.012062    00:24:17:1f:43:95     Lite-OnT_bf:dd:4a     EAPOL    Key
      8 1.012561    Lite-OnT_bf:dd:4a     00:24:17:1f:43:95     EAPOL    Key
      9 1.340060    fe80::216:44ff:febf:dd4a ff02::2               ICMPv6   Router solicitation
     10 2.834205    00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.77?  Tell 192.168.1.254
     11 2.835078    00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     12 2.836132    00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.65?  Tell 192.168.1.254
     13 2.837054    00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     14 2.838161    00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.64?  Tell 192.168.1.254
     15 5.340032    fe80::216:44ff:febf:dd4a ff02::2               ICMPv6   Router solicitation
     16 6.792031    fe80::216:44ff:febf:dd4a ff02::16              ICMPv6   Multicast Listener Report Message v2
     17 9.340031    fe80::216:44ff:febf:dd4a ff02::2               ICMPv6   Router solicitation
     18 25.537198   0.0.0.0               255.255.255.255       DHCP     DHCP Request  - Transaction ID 0x374fb673
     19 25.570321   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.77?  Tell 192.168.1.254
     20 26.488518   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.77?  Tell 192.168.1.254
     21 26.553279   192.168.1.254         192.168.1.77          DHCP     DHCP ACK      - Transaction ID 0x374fb673
     22 26.587954   192.168.1.77          224.0.0.22            IGMP     V3 Membership Report / Join group 224.0.0.251 for any sources
     23 26.688102   192.168.1.77          224.0.0.251           MDNS     Standard query PTR _pgpkey-hkp._tcp.local, "QM" question
     24 26.816250   192.168.1.77          224.0.0.251           MDNS     Standard query ANY      25 26.856159   192.168.1.77          
     26 27.068242   192.168.1.77          224.0.0.251           MDNS     Standard query ANY      27 27.320311   192.168.1.77               
      28 27.520556   192.168.1.77          224.0.0.251           MDNS     Standard query response PTR, cache flush user-PC.local A, cache flush 
     29 27.688161   192.168.1.77          224.0.0.251           MDNS     Standard query PTR _pgpkey-hkp._tcp.local, "QM" question
     30 28.037220   192.168.1.77          224.0.0.251           MDNS     Standard query response PTR _workstation._tcp.local PTR user-PC     
     31 28.700497   192.168.1.77          224.0.0.251           MDNS     Standard query response PTR, cache flush user-PC.local A, cache flush 
     32 29.696120   192.168.1.77          224.0.0.251           MDNS     Standard query PTR _pgpkey-hkp._tcp.local, "QM" question
     33 30.216231   192.168.1.77          224.0.0.251           MDNS     Standard query response PTR _workstation._tcp.local PTR user-PC 
     34 30.880448   192.168.1.77          224.0.0.251           MDNS     Standard query response PTR, cache flush user-PC.local A, cache flush 
     35 31.248038   192.168.1.77          224.0.0.22            IGMP     V3 Membership Report / Join group 224.0.0.251 for any sources
     36 32.939932   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.77?  Tell 192.168.1.254
     37 32.939973   Lite-OnT_bf:dd:4a     00:24:17:1f:43:94     ARP      192.168.1.77 is at 00:16:44:bf:dd:4a
     38 32.940851   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     39 32.941875   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.65?  Tell 192.168.1.254
     40 32.942880   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     41 32.944335   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.64?  Tell 192.168.1.254
     42 33.700131   192.168.1.77          224.0.0.251           MDNS     Standard query PTR _pgpkey-hkp._tcp.local, "QM" question
     43 41.708106   192.168.1.77          224.0.0.251           MDNS     Standard query PTR _pgpkey-hkp._tcp.local, "QM" question
     44 48.746801   192.168.1.77          192.168.1.254         DNS      Standard query A user-PC.config
     45 48.749414   192.168.1.254         192.168.1.77          DNS      Standard query response A 192.168.1.77
     46 48.884785   192.168.1.77          192.168.1.254         DNS      Standard query A user-PC.config
     47 48.887567   192.168.1.254         192.168.1.77          DNS      Standard query response A 192.168.1.77
     48 53.744449   Lite-OnT_bf:dd:4a     00:24:17:1f:43:94     ARP      Who has 192.168.1.254?  Tell 192.168.1.77
     49 53.745783   00:24:17:1f:43:94     Lite-OnT_bf:dd:4a     ARP      192.168.1.254 is at 00:24:17:1f:43:94
     50 57.712020   192.168.1.77          224.0.0.251           MDNS     Standard query PTR _pgpkey-hkp._tcp.local, "QM" question
     51 62.738309   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.77?  Tell 192.168.1.254
     52 62.738334   Lite-OnT_bf:dd:4a     00:24:17:1f:43:94     ARP      192.168.1.77 is at 00:16:44:bf:dd:4a
     53 62.739301   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     54 62.740339   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.65?  Tell 192.168.1.254
     55 62.741391   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     56 62.742399   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.64?  Tell 192.168.1.254
     57 71.618495   192.168.1.77          192.168.1.254         ICMP     Echo (ping) request
     58 71.620885   192.168.1.254         192.168.1.77          ICMP     Echo (ping) reply
     59 71.672729   192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
     60 71.954468   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.65?  Tell 192.168.1.254
     61 71.954501   Lite-OnT_bf:dd:4a     00:24:17:1f:43:94     ARP      192.168.1.65 is at 00:16:44:bf:dd:4a
     62 71.955942   192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - Transaction ID 0x5d155a05
     63 77.536127   192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
     64 77.541404   192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - Transaction ID 0x5d155a05
     65 84.536124   192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
     66 84.541455   192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - Transaction ID 0x5d155a05
     67 89.712143   192.168.1.77          224.0.0.251           MDNS     Standard query PTR _pgpkey-hkp._tcp.local, "QM" question
     68 91.525473   192.168.1.77          192.168.1.254         DNS      Standard query A [www.yahoo.com]("http://www.yahoo.com")
     69 91.552470   192.168.1.254         192.168.1.77          DNS      Standard query response CNAME [www.wa1.b.yahoo.com]("http://www.wa1.b.yahoo.com") CNAME www-     
      70 91.552826   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
      71 91.590342   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     72 92.561053   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     73 92.591023   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     74 92.844067   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.65?  Tell 192.168.1.254
     75 92.844092   Lite-OnT_bf:dd:4a     00:24:17:1f:43:94     ARP      192.168.1.65 is at 00:16:44:bf:dd:4a
     76 92.845105   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     77 92.846198   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.65?  Tell 192.168.1.254
     78 92.846218   Lite-OnT_bf:dd:4a     00:24:17:1f:43:94     ARP      192.168.1.65 is at 00:16:44:bf:dd:4a
     79 92.847180   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.66?  Tell 192.168.1.254
     80 92.848130   00:24:17:1f:43:94     Broadcast             ARP      Who has 192.168.1.64?  Tell 192.168.1.254
     81 93.561059   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     82 93.591035   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     83 94.561056   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     84 94.590848   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     85 95.560060   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     86 95.604716   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     87 96.560059   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     88 96.589967   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     89 97.560062   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     90 97.590157   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     91 98.560031   Lite-OnT_bf:dd:4a     00:24:17:1f:43:94     ARP      Who has 192.168.1.254?  Tell 192.168.1.77
     92 98.560055   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     93 98.561560   00:24:17:1f:43:94     Lite-OnT_bf:dd:4a     ARP      192.168.1.254 is at 00:24:17:1f:43:94
     94 98.590763   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     95 99.560056   192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     96 99.589856   87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     97 100.560052  192.168.1.77          87.248.113.14         ICMP     Echo (ping) request
     98 100.589429  87.248.113.14         192.168.1.77          ICMP     Echo (ping) reply
     99 104.536141  192.168.1.77          192.168.1.254         DHCP     DHCP Request  - Transaction ID 0x5d155a05
    100 104.541755  192.168.1.254         192.168.1.65          DHCP     DHCP ACK      - Transaction ID 0x5d155a05

---

