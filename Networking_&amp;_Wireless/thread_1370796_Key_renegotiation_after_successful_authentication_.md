---
title: "Key renegotiation after successful authentication with wpa_supplicant"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by 11ghjones on 2010-01-02
Hi, I'm using a WN121T Netgear USB Wireless adapter and after several failed attempts using different GUIs (nm-applet, wicd), I decided to manually configure my WPA network with wpa_supplicant and the ifup/ifdown tools.  I can occasionally get my network up and running, after which I remain online until disconnect.  I use the commands in sequence (as root):

```

wpa_supplicant -c /etc/wpa_supplicant.conf -D wext -i wlan0 &
ifconfig wlan0 192.168.2.5
route add default gw 192.168.2.1 wlan0

```

And my wpa_supplicant.conf is set up as follows:
```

network={
	ssid="greg"
	#psk="<removed for privacy>"
	psk=cfeb2ff15a98be86431848ac6aa34d8c2a6dcadda91e6c072842c4ac51b8846a
}

```

Sometimes, however, if I do not set up the static ip address quickly enough, wpa_supplicant will, after successfully authenticating, try to continue negotiating keys, and at that point, the connection is lost and I must kill wpa_supplicant and start over.  Any ideas on what is happening here?

---

### Post by 11ghjones on 2010-01-02
I've attached the debug output of wpa_supplicant if that helps...

---

### Post by 11ghjones on 2010-01-04
No ideas from anyone...?

---

### Post by 11ghjones on 2010-01-17
Sorry to revive this after so long, but I'm still experiencing the same problem, and I forgot to mention that this method only works about 1 in 5 tries.  I have no clue what is going on.  Any ideas on how to make this process a bit easier or at least automated?

---

### Post by MarkC502 on 2010-01-17
[FONT=monospace]I will try to help you out a little if I can. I have never configured WPA via scripts but I do write all kinds of scripts for my wifi devices to configure them for other purposes ( such as long range links and monitor mode for snooping ). I would say you need to read the man page on wpa_supplicant and see if you are using the right options, O did and quickly saw 2 things that might solve the equation.

First is that they call for standard use to be with a -B to fork the proccess to the background which you are not using. Worth a try.

Second I see a -W option that says "wait for control interface before starting. Worth a try.

 
TRY INSTEAD OF THIS[/FONT]
wpa_supplicant -c /etc/wpa_supplicant.conf -D wext -i wlan0 &
ifconfig wlan0 192.168.2.5
THIS

wpa_supplicant -B -d -K -W -i wlan0 -c /etc/wpa_supplicant.conf -D wext &
ifconfig wlan0 192.168.2.5

Which would add the following

-B to fork to a background daemon proccess

-W to wait for interface before starting

-K include keys in debug output ( to see what it is sending etc )

-d to increase debug verbosity ( spit more stuff out )

Also you could try not including the -D wext and let it try to use the default and see if that works for you.

Good Luck

---

### Post by 11ghjones on 2010-01-17
Thank you!  I'll give that a try.  The only reason I wasn't using -B was so I could run it in the foreground to see debugging output, etc. and I could time the ifconfig command precisely.

---

### Post by 11ghjones on 2010-01-17
Normal Config (no -K, no -W, -D wext)

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='greg'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:4d:77:e4:f1
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): ba ee f9 2c ff c1 57 cc 82 e2 25 e7 e0 d7 c6 69
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     67 72 65 67                                       greg            
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 782 bytes of scan results (3 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:df:22:ad:8d ssid='greg' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:1c:df:22:ad:8d ssid='greg'
Trying to associate with 00:1c:df:22:ad:8d (SSID='greg' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
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
Wireless event: cmd=0x8c07 len=63
AssocReq IE wireless event - hexdump(len=55): 00 04 67 72 65 67 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 07 00 50 f2 02 00 01 00 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=62
AssocResp IE wireless event - hexdump(len=54): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 07 00 0c 43 04 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:df:22:ad:8d
Association info event
req_ies - hexdump(len=55): 00 04 67 72 65 67 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 07 00 50 f2 02 00 01 00 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
resp_ies - hexdump(len=54): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 07 00 0c 43 04 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
RSN: PMKID from assoc IE not found from PMKSA cache
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:df:22:ad:8d
No keys have been configured - skip key clearing
Associated with 00:1c:df:22:ad:8d
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
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1c:df:22:ad:8d
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=117
  EAPOL-Key type=2
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=22
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 9d
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 17
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
RSN: msg 1/4 key data - hexdump(len=22): dd 14 00 0f ac 04 a1 b7 28 ae 8f 77 fc 8b d4 d9 cf 80 12 61 dd aa
RSN: PMKID from Authenticator - hexdump(len=16): a1 b7 28 ae 8f 77 fc 8b d4 d9 cf 80 12 61 dd aa
RSN: no matching PMKID found
WPA: Renewed SNonce - hexdump(len=32): 0c 04 85 c4 4b 48 3d c7 cb fc 70 5d 7e 77 0b 0c 76 46 21 47 64 7d a4 9a e7 d4 b3 18 b4 2b e1 c8
WPA: PTK derivation - A1=00:18:4d:77:e4:f1 A2=00:1c:df:22:ad:8d
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:1c:df:22:ad:8d
IEEE 802.1X RX: version=1 type=3 length=157
  EAPOL-Key type=2
  key_info 0x13c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=32 key_data_length=62
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 9e
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 17
  key_iv - hexdump(len=16): f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 3b 32 8b 52 a8 52 d7 b3 80 57 fe 13 05 19 ab 04
RSN: encrypted key data - hexdump(len=62): 0a 1e d0 57 47 76 1c a3 96 3a 91 c8 f0 5a 3a ba 3a 70 f0 1b 57 9b 6b 31 ee d8 16 66 fc a3 d3 f3 29 ae 55 4f 40 cb 51 b6 17 b2 72 09 3e 63 b3 8e a4 a8 23 7a 6b db c1 09 a7 82 5d e2 c5 3e
WPA: decrypted EAPOL-Key key data - hexdump(len=62): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
WPA: IE KeyData - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): [REMOVED]
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:1c:df:22:ad:8d [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1c:df:22:ad:8d completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x1 index=0 bssid=00:1c:df:22:ad:8d
RSN: PMKID candidate event - bssid=00:1c:df:22:ad:8d index=0 preauth=1
RSN: added PMKSA cache candidate 00:1c:df:22:ad:8d prio 0
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
CTRL-EVENT-TERMINATING - signal 15 received
Removing interface wlan0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
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
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='greg'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:4d:77:e4:f1
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): ba ee f9 2c ff c1 57 cc 82 e2 25 e7 e0 d7 c6 69
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     67 72 65 67                                       greg            
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1077 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:df:22:ad:8d ssid='greg' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:1c:df:22:ad:8d ssid='greg'
Trying to associate with 00:1c:df:22:ad:8d (SSID='greg' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
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
Wireless event: cmd=0x8c07 len=63
AssocReq IE wireless event - hexdump(len=55): 00 04 67 72 65 67 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 07 00 50 f2 02 00 01 00 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=62
AssocResp IE wireless event - hexdump(len=54): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 07 00 0c 43 04 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:df:22:ad:8d
Association info event
req_ies - hexdump(len=55): 00 04 67 72 65 67 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 07 00 50 f2 02 00 01 00 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
resp_ies - hexdump(len=54): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 07 00 0c 43 04 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
RSN: PMKID from assoc IE not found from PMKSA cache
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:df:22:ad:8d
No keys have been configured - skip key clearing
Associated with 00:1c:df:22:ad:8d
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
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1c:df:22:ad:8d
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=117
  EAPOL-Key type=2
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=22
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 9f
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 19
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
RSN: msg 1/4 key data - hexdump(len=22): dd 14 00 0f ac 04 a1 b7 28 ae 8f 77 fc 8b d4 d9 cf 80 12 61 dd aa
RSN: PMKID from Authenticator - hexdump(len=16): a1 b7 28 ae 8f 77 fc 8b d4 d9 cf 80 12 61 dd aa
RSN: no matching PMKID found
WPA: Renewed SNonce - hexdump(len=32): 7e 7a 6a e4 bc 6b 1d 55 43 1c 5c 24 43 13 44 79 87 31 64 cf 07 42 41 9e 90 2a 64 97 0f b0 5b ac
WPA: PTK derivation - A1=00:18:4d:77:e4:f1 A2=00:1c:df:22:ad:8d
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:1c:df:22:ad:8d
IEEE 802.1X RX: version=1 type=3 length=157
  EAPOL-Key type=2
  key_info 0x13c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=32 key_data_length=62
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 a0
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 19
  key_iv - hexdump(len=16): f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): bb 59 71 06 33 8d f5 a4 fb 8c db 1b bb 09 fb 2f
RSN: encrypted key data - hexdump(len=62): f6 ad ed 8a 97 87 74 1d 3a c4 9a a4 1f 53 40 c0 75 0a 01 41 d2 04 d0 f5 66 e0 ad 90 3b 68 3f e0 e5 a4 08 50 17 2b f6 3e 71 11 14 94 7c 84 74 80 72 0f 81 6c ac ac fe 29 b0 c2 17 8e a8 a5
WPA: decrypted EAPOL-Key key data - hexdump(len=62): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
WPA: IE KeyData - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): [REMOVED]
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:1c:df:22:ad:8d [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1c:df:22:ad:8d completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x1 index=0 bssid=00:1e:58:e8:d9:5d
RSN: PMKID candidate event - bssid=00:1e:58:e8:d9:5d index=0 preauth=1
RSN: added PMKSA cache candidate 00:1e:58:e8:d9:5d prio 0
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x1 index=1 bssid=00:1c:df:22:ad:8d
RSN: PMKID candidate event - bssid=00:1c:df:22:ad:8d index=1 preauth=1
RSN: added PMKSA cache candidate 00:1c:df:22:ad:8d prio 1
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication

```

And after a killall wpa_supplicant

```
CTRL-EVENT-TERMINATING - signal 15 received
Removing interface wlan0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
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
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

```

I'll post the other debug logs as well.

---

### Post by 11ghjones on 2010-01-17
Normal Configuration with the -K option added

```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='greg'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:4d:77:e4:f1
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): ba ee f9 2c ff c1 57 cc 82 e2 25 e7 e0 d7 c6 69
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     67 72 65 67                                       greg            
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 782 bytes of scan results (3 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:df:22:ad:8d ssid='greg' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:1c:df:22:ad:8d ssid='greg'
Trying to associate with 00:1c:df:22:ad:8d (SSID='greg' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
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
Wireless event: cmd=0x8c07 len=63
AssocReq IE wireless event - hexdump(len=55): 00 04 67 72 65 67 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 07 00 50 f2 02 00 01 00 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=62
AssocResp IE wireless event - hexdump(len=54): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 07 00 0c 43 04 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:df:22:ad:8d
Association info event
req_ies - hexdump(len=55): 00 04 67 72 65 67 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 07 00 50 f2 02 00 01 00 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
resp_ies - hexdump(len=54): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 07 00 0c 43 04 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
RSN: PMKID from assoc IE not found from PMKSA cache
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:df:22:ad:8d
No keys have been configured - skip key clearing
Associated with 00:1c:df:22:ad:8d
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
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1c:df:22:ad:8d
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=117
  EAPOL-Key type=2
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=22
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 a5
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 1f
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
RSN: msg 1/4 key data - hexdump(len=22): dd 14 00 0f ac 04 a1 b7 28 ae 8f 77 fc 8b d4 d9 cf 80 12 61 dd aa
RSN: PMKID from Authenticator - hexdump(len=16): a1 b7 28 ae 8f 77 fc 8b d4 d9 cf 80 12 61 dd aa
RSN: no matching PMKID found
WPA: Renewed SNonce - hexdump(len=32): 8c ed 56 a2 68 c0 5c 1d 0c 94 06 b3 42 f0 60 2b 45 33 19 8b 99 07 aa 04 cf 3e 98 b6 a6 1d 8c d9
WPA: PTK derivation - A1=00:18:4d:77:e4:f1 A2=00:1c:df:22:ad:8d
WPA: PMK - hexdump(len=32): cf eb 2f f1 5a 98 be 86 43 18 48 ac 6a a3 4d 8c 2a 6d ca dd a9 1e 6c 07 28 42 c4 ac 51 b8 84 6a
WPA: PTK - hexdump(len=64): 0f de 83 eb 96 be 9e 51 4a 81 e5 46 9d 4f 91 0d 81 6d 26 90 df 15 91 8a 91 20 78 e1 aa 2c c7 3b a1 ac 7c 7b 33 0b d7 4b ad f3 0f ea d4 70 0f 60 2d fa a0 13 39 5e 5d de be 98 76 d4 38 1d f9 b7
WPA: WPA IE for msg 2/4 - hexdump(len=24): 30 16 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 0c 00 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:1c:df:22:ad:8d
IEEE 802.1X RX: version=1 type=3 length=157
  EAPOL-Key type=2
  key_info 0x13c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=32 key_data_length=62
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 a6
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 1f
  key_iv - hexdump(len=16): f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 4a fa 6c ee 1d 34 0c 59 c2 c3 8b db b0 d4 91 0b
RSN: encrypted key data - hexdump(len=62): ed 92 a1 c6 a5 52 b8 ed 90 84 70 cc 33 69 61 a7 0b 6a b2 3b b9 c5 98 56 27 d3 ad 06 4c a2 d7 c0 a6 f8 8d 4c e0 c8 2c bd 37 38 0d e5 b2 d4 1a d5 a5 3a 51 36 06 28 84 50 d9 bb 6e f7 03 0b
WPA: decrypted EAPOL-Key key data - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
WPA: IE KeyData - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Group Key - hexdump(len=32): 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:1c:df:22:ad:8d [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1c:df:22:ad:8d completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x1 index=0 bssid=00:1c:df:22:ad:8d
RSN: PMKID candidate event - bssid=00:1c:df:22:ad:8d index=0 preauth=1
RSN: added PMKSA cache candidate 00:1c:df:22:ad:8d prio 0
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RX EAPOL from 00:1c:df:22:ad:8d
IEEE 802.1X RX: version=1 type=3 length=157
  EAPOL-Key type=2
  key_info 0x13c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=32 key_data_length=62
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 a7
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 1f
  key_iv - hexdump(len=16): f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): d5 37 3a fd b7 4f fa f3 62 ca 8d 2e 37 95 0c dd
RSN: encrypted key data - hexdump(len=62): ed 92 a1 c6 a5 52 b8 ed 90 84 70 cc 33 69 61 a7 0b 6a b2 3b b9 c5 98 56 27 d3 ad 06 4c a2 d7 c0 a6 f8 8d 4c e0 c8 2c bd 37 38 0d e5 b2 d4 1a d5 a5 3a 51 36 06 28 84 50 d9 bb 6e f7 03 0b
WPA: decrypted EAPOL-Key key data - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
WPA: IE KeyData - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Group Key - hexdump(len=32): 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:1c:df:22:ad:8d [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x1 index=0 bssid=00:1c:df:22:ad:8d
RSN: PMKID candidate event - bssid=00:1c:df:22:ad:8d index=0 preauth=1
RSN: added PMKSA cache candidate 00:1c:df:22:ad:8d prio 0
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RX EAPOL from 00:1c:df:22:ad:8d
IEEE 802.1X RX: version=1 type=3 length=157
  EAPOL-Key type=2
  key_info 0x13c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=32 key_data_length=62
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 a8
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 1f
  key_iv - hexdump(len=16): f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): bd 20 7e 9c 90 ff b8 12 87 8d b7 32 eb 27 78 96
RSN: encrypted key data - hexdump(len=62): ed 92 a1 c6 a5 52 b8 ed 90 84 70 cc 33 69 61 a7 0b 6a b2 3b b9 c5 98 56 27 d3 ad 06 4c a2 d7 c0 a6 f8 8d 4c e0 c8 2c bd 37 38 0d e5 b2 d4 1a d5 a5 3a 51 36 06 28 84 50 d9 bb 6e f7 03 0b
WPA: decrypted EAPOL-Key key data - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
WPA: IE KeyData - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Group Key - hexdump(len=32): 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:1c:df:22:ad:8d [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x1 index=0 bssid=00:1c:df:22:ad:8d
RSN: PMKID candidate event - bssid=00:1c:df:22:ad:8d index=0 preauth=1
RSN: added PMKSA cache candidate 00:1c:df:22:ad:8d prio 0
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RX EAPOL from 00:1c:df:22:ad:8d
IEEE 802.1X RX: version=1 type=3 length=157
  EAPOL-Key type=2
  key_info 0x13c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=32 key_data_length=62
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 06 a9
  key_nonce - hexdump(len=32): 94 4b d9 8b b2 31 9c 87 79 4f 1e 6b 32 be c3 f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51 1f
  key_iv - hexdump(len=16): f1 2c 7d 8c 08 12 5d fe ed 32 07 c1 b0 36 4e 51
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): cf cf bd 2a 91 a5 4c c3 ca 16 cc 02 12 fe 13 ec
RSN: encrypted key data - hexdump(len=62): ed 92 a1 c6 a5 52 b8 ed 90 84 70 cc 33 69 61 a7 0b 6a b2 3b b9 c5 98 56 27 d3 ad 06 4c a2 d7 c0 a6 f8 8d 4c e0 c8 2c bd 37 38 0d e5 b2 d4 1a d5 a5 3a 51 36 06 28 84 50 d9 bb 6e f7 03 0b
WPA: decrypted EAPOL-Key key data - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:df:22:ad:8d (ver=1)
WPA: IE KeyData - hexdump(len=62): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): 01 00 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Group Key - hexdump(len=32): 37 91 98 cb d0 56 7f 0d 59 a6 d2 44 42 34 8f 35 e3 e1 10 39 32 17 2d 03 69 8a 57 c6 28 25 9b 18
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:1c:df:22:ad:8d [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x1 index=0 bssid=00:1c:df:22:ad:8d
RSN: PMKID candidate event - bssid=00:1c:df:22:ad:8d index=0 preauth=1
RSN: added PMKSA cache candidate 00:1c:df:22:ad:8d prio 0
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
```

---

### Post by 11ghjones on 2010-01-17
With -W and -K (still using wext)

```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='greg'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:4d:77:e4:f1
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): ba ee f9 2c ff c1 57 cc 82 e2 25 e7 e0 d7 c6 69
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
CTRL_IFACE - wlan0 - wait for monitor to attach
recvfrom(ctrl_iface): Bad file descriptor
```

The last two lines repeat themselves over and over.

---

### Post by 11ghjones on 2010-01-17
With -W and default driver (no -D option)

```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='greg'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:4d:77:e4:f1
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): ba ee f9 2c ff c1 57 cc 82 e2 25 e7 e0 d7 c6 69
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
CTRL_IFACE - wlan0 - wait for monitor to attach
```

Last line repeated indefinitely.

---

