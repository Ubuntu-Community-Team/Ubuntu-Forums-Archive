---
title: "Can't conect to WPA network, to WEP encrypted yes."
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by peterpan73 on 2008-12-17
Hi,
at first sorry for my english (it's not my strong point).

As in title - I can conect to my home network encrypted WEP (64bit) but I can't conect when network is encrypted WPA. I use ndiswrapper to my wifi card (D-link DWL-G520+) and i have installed wpasupplicant.
On fresh instaled ubu 8.04 at first I try this: [http://ubuntu-tutorials.blogspot.com/2007/02/enable-wpa-wireless-access-point-in.html](http://ubuntu-tutorials.blogspot.com/2007/02/enable-wpa-wireless-access-point-in.html) - doesn't work i havn't WPA option (I try on native drivers acx111 and on ndiswrapper). Later I try this: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy_pl#Jak_uruchomi.C4.87_WPA_ze_sterownikami_Ndiswrapper](http://ubuntuguide.org/wiki/Ubuntu:Gutsy_pl#Jak_uruchomi.C4.87_WPA_ze_sterownikami_Ndiswrapper) - system crash. I try else this - [http://ubuntuforums.org/showthread.php?t=262194](http://ubuntuforums.org/showthread.php?t=262194) - without good results. Finnaly I deinstall network manager and install wicd - it "see" my network and I can take WPA encryption - but when I try connect wicd validating encryption and ... not conected! (passphrase have only english letter end number). In wicd i try as wpasupplicant driver wext, ndiswrapper and other drivers.
I'm quite newbie in linux. If someone have any good ideas for me I will be gratefull for help. If more information are needed (logs, ect.) please write me where or how can I find it.

---

### Post by spawn. on 2008-12-17
You aren't the only one in this boat. I had issues with this as well. I had to configure everything by hand to suit my particular wireless card. In other cases, where there are different wireless cards, it will be an issue with the hardware (as far as compatibility with whatever software you're running). Correct me if I'm wrong, but this is just what I've experienced on a second laptop running Ubuntu. The only operating systems that I found to be the best all around when connecting to all sorts of networks (usually well encrypted such as a university network) is Windows and Mac operating systems.

---

### Post by kevdog on 2008-12-17
Have you tried to manually connect to generate any error messages that may help solve the problem?

A link is in my signature and I would be happy to help you (if you give me something to go on?)

---

### Post by peterpan73 on 2008-12-17
So...
Wicd and network manager deinstaled. Ndiswrapper loaded and start with system (add to /etc/modules) acx driver blacklisted (added to /etc/modprobe.d/blacklist). Wpasupplicant instaled (present in synaptic ver. 0.6.0+0.5.8 ). File /etc/wpa_supplicant.conf created (as in Your tutorial). System restarted.
Terminal:
```
piotr@piotr-desktop:~$ sudo ifconfig wlan0 down
piotr@piotr-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:15:f1:06
Sending on   LPF/wlan0/00:11:95:15:f1:06
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.15.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
```

and:
 ```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
```

give me this (its part, but i think so it repeats -I wait 5 min. and console whole time "work")
```
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=55
AssocReq IE wireless event - hexdump(len=47): 00 04 70 65 74 65 01 05 82 84 8b 96 2c 32 08 0c 12 18 24 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=25
AssocResp IE wireless event - hexdump(len=17): 01 05 82 84 8b 96 2c 32 08 0c 12 18 24 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1a:70:86:60:39
Association info event
req_ies - hexdump(len=47): 00 04 70 65 74 65 01 05 82 84 8b 96 2c 32 08 0c 12 18 24 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=17): 01 05 82 84 8b 96 2c 32 08 0c 12 18 24 30 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: SCANNING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1a:70:86:60:39
No keys have been configured - skip key clearing
Associated with 00:1a:70:86:60:39
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:1a:70:86:60:39
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1a:70:86:60:39 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): dc 94 5a bb 2d 9e ff 77 cc 5a ce c7 19 b5 7c dc a3 3a 15 bd 47 ac 03 cf f8 27 ff 77 32 c3 07 f1
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 dc 94 5a bb 2d 9e ff 77 cc 5a ce c7 19 b5 7c dc a3 3a 15 bd 47 ac 03 cf f8 27 ff 77 32 c3 07 f1 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ed 35 86 15 7c 64 13 4f 07 68 fe a0 fe a8 65 c0 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1a:70:86:60:39
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 94 35 65 56 03 f3 4b 19 c6 de 7d 6c f0 85 57 4d 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 94 35 65 56 03 f3 4b 19 c6 de 7d 6c f0 85 57 4d
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 94 35 65 56 03 f3 4b 19 c6 de 7d 6c f0 85 57 4d 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1a:70:86:60:39 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2a 68 97 d9 96 ab 54 d6 05 08 ec 8d 19 b8 ee 2e 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
Scan timeout - try to get results
Received 261 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1a:70:86:60:39 ssid='pete' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - blacklisted
Try to find non-WPA AP
0: 00:1a:70:86:60:39 ssid='pete' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - blacklisted
No APs found - clear blacklist and try again
Removed BSSID 00:1a:70:86:60:39 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1a:70:86:60:39 ssid='pete' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1a:70:86:60:39 ssid='pete'
Try to find non-WPA AP
Already associated with the selected AP.
RX EAPOL from 00:1a:70:86:60:39
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 03 c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0b e2 37 ec 77 62 ae 4c 68 96 b3 41 5e e6 48 09 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 0b e2 37 ec 77 62 ae 4c 68 96 b3 41 5e e6 48 09
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 03 c6 90 e1 50 32 82 4d 5a c0 d1 af 80 18 21 6d 07 38 5e a9 97 4f 46 ac 65 0e 52 39 c6 93 4c d1 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0b e2 37 ec 77 62 ae 4c 68 96 b3 41 5e e6 48 09 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1a:70:86:60:39 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1d c2 86 34 e4 c0 bb 92 4c 60 dc 72 84 80 24 4d 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
```

---

