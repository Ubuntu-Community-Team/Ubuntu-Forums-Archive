---
title: "wpa_supplicant throws kernel oops with ralink rt3562sta ralink"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by kgoess on 2011-12-22
I have a  ralink rt3562sta on my desktop and am seeing this kernel oops every time the card reconnects.  The first time is ok as long as I insmod it by hand, but after that if the connection drops or if I try to wake up after hibernate, I get a kernel oops every time.  

The line that stands out for me is 

   ```
process wpa_supplicant (pid:13802 threadinfo...)
```

I'm using the driver from DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 and have tried both the rt2860.bin firmware that came with 11.10 as well as the firmware from Ralink. rt2x00pci and rt2800pci are both blacklisted.

Any suggestion would be appreciated!

[IMG]http://i41.tinypic.com/ao3z7.jpg[/IMG]

This is an expansion on my other thread asking about the oopses in general, but I see now that it's related to network reconnectsm and that one never generated any interest :-( [http://ubuntuforums.org/showthread.php?t=1892663](http://ubuntuforums.org/showthread.php?t=1892663)

---

### Post by praseodym on 2011-12-22
Hi,

try to start the supplicant in debug mode:

```
gksu gedit /etc/wpa_supplicant/wpa_supplicant.conf 
```
Add:
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
ssid="[COLOR="Red"]YourESSID[/COLOR]"
scan_ssid=1
proto=WPA RSN
key_mgmt=WPA-PSK
pairwise=TKIP CCMP
group=TKIP CCMP
psk="[COLOR="Red"]YourKey[/COLOR]"
}
```
save, close the editor, and:
```
sudo service network-manager stop
sudo killall wpa_supplicant
sudo wpa_supplicant -i [COLOR="Red"]wlan0[/COLOR] -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d 
```
Check your interface name.

Stop the supplicant after 30 s with CTRL+C and show the output.

In a second terminal you can try:

```
sudo dhclient [COLOR="Red"]wlan0[/COLOR] 
```
in parallel

---

### Post by kgoess on 2011-12-23
Thanks for the response!

This driver puts the interface on ra0, not wlan0,  using wlan0 does this:

kevin@kazimir:~$ sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 0
   id=0 ssid='nemo'
Could not read interface wlan0 flags: No such device
Failed to initialize driver interface
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout


Using ra0 does this:


```


$ sudo wpa_supplicant -i ra0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d
Initializing interface 'ra0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 0
   id=0 ssid='nemo'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=14 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: c8:3a:35:c8:27:5d
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 62 da e9 de 15 bb 53 d1 b8 c2 85 5b 9c ce 98 cd
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface ra0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=12
State: DISCONNECTED -> SCANNING
Scan SSID - hexdump_ascii(len=4):
     6e 65 6d 6f                                       nemo            
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
EAPOL: Supplicant port status: Unauthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b19 len=16
Received 1334 bytes of scan results (7 BSSes)
BSS: Start scan result update 1
BSS: Add new id 0 BSSID 00:1e:58:0e:bc:76 SSID 'dlink'
BSS: Add new id 1 BSSID c8:64:c7:8e:44:93 SSID 'Livebox-4493'
BSS: Add new id 2 BSSID d0:15:4a:fd:72:12 SSID 'Livebox'
BSS: Add new id 3 BSSID 00:23:8e:de:cd:8f SSID 'NETIA-DECD8D'
BSS: Add new id 4 BSSID 00:21:29:b5:dc:7c SSID 'nemo'
BSS: Add new id 5 BSSID 00:1f:1f:47:ad:c4 SSID 'lamus'
BSS: Add new id 6 BSSID 00:19:e0:8c:18:bc SSID 'KSI_Romek'
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:58:0e:bc:76 ssid='dlink' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: c8:64:c7:8e:44:93 ssid='Livebox-4493' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
2: d0:15:4a:fd:72:12 ssid='Livebox' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
3: 00:23:8e:de:cd:8f ssid='NETIA-DECD8D' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:21:29:b5:dc:7c ssid='nemo' wpa_ie_len=0 rsn_ie_len=24 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:21:29:b5:dc:7c ssid='nemo'
Trying to associate with 00:21:29:b5:dc:7c (SSID='nemo' freq=2437 MHz)
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 0c 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_psk
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP fail=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portControl=Auto
EAPOL: Supplicant port status: Unauthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b1a len=20
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8c07 len=54
AssocReq IE wireless event - hexdump(len=38): 00 04 6e 65 6d 6f 01 08 82 84 8b 96 24 b0 48 6c 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:21:29:b5:dc:7c
Association info event
req_ies - hexdump(len=38): 00 04 6e 65 6d 6f 01 08 82 84 8b 96 24 b0 48 6c 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:21:29:b5:dc:7c
No keys have been configured - skip key clearing
Associated with 00:21:29:b5:dc:7c
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:21:29:b5:dc:7c
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=2 type=3 length=117
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=22
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 09
  key_nonce - hexdump(len=32): 89 b0 cd 0f 09 40 b5 c8 42 b0 72 b9 f1 04 e4 da e3 f1 01 5c f6 b5 9c d0 5e 03 7c fe 2d 4a 21 8e
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:21:29:b5:dc:7c (ver=2)
RSN: msg 1/4 key data - hexdump(len=22): dd 14 00 0f ac 04 46 19 9a 9b c9 59 0e cd 59 37 c1 27 a5 70 ad 46
WPA: PMKID in EAPOL-Key - hexdump(len=22): dd 14 00 0f ac 04 46 19 9a 9b c9 59 0e cd 59 37 c1 27 a5 70 ad 46
RSN: PMKID from Authenticator - hexdump(len=16): 46 19 9a 9b c9 59 0e cd 59 37 c1 27 a5 70 ad 46
RSN: no matching PMKID found
WPA: Renewed SNonce - hexdump(len=32): e5 34 a7 dc 04 c8 b6 d0 50 2b 72 e4 1c f6 65 bb 0e 89 a7 ad 0a 8b 0e bd 37 e4 e4 3f 8d f2 60 01
WPA: PTK derivation - A1=c8:3a:35:c8:27:5d A2=00:21:29:b5:dc:7c
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=48): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:21:29:b5:dc:7c
IEEE 802.1X RX: version=2 type=3 length=175
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=80
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 0a
  key_nonce - hexdump(len=32): 89 b0 cd 0f 09 40 b5 c8 42 b0 72 b9 f1 04 e4 da e3 f1 01 5c f6 b5 9c d0 5e 03 7c fe 2d 4a 21 8e
  key_iv - hexdump(len=16): e3 f1 01 5c f6 b5 9c d0 5e 03 7c fe 2d 4a 21 8f
  key_rsc - hexdump(len=8): 29 15 05 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): a8 7e 27 26 67 6f 84 a5 e1 a0 44 c4 58 28 db 9c
RSN: encrypted key data - hexdump(len=80): b1 80 68 c7 a9 79 38 c4 54 66 c7 13 9a 30 52 32 fc d6 fc 63 95 00 15 c3 a0 56 f4 b4 fd 4d 03 2e e9 fa 53 1b 46 8d 35 68 fe 99 e0 1c 6e 1f 6d fe 9f 4b c6 76 75 73 07 9a 64 0e 5c 23 e6 a3 ef 64 bd c2 b0 20 fa e0 5e a3 b9 c0 40 d2 3f 16 3d 68
WPA: decrypted EAPOL-Key key data - hexdump(len=72): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:21:29:b5:dc:7c (ver=2)
WPA: IE KeyData - hexdump(len=72): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 0c 00 dd 26 00 0f ac 01 02 00 43 0c 64 74 b2 7b 67 61 08 3c d7 05 c5 38 e2 26 75 8e 57 fb e0 65 77 b8 7b e5 67 8c ef f9 d5 a7 dd 00 00 00 00 00
WPA: RSN IE in EAPOL-Key - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 0c 00
WPA: GTK in EAPOL-Key - hexdump(len=40): [REMOVED]
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): [REMOVED]
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
WPA: RSC - hexdump(len=6): 29 15 05 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:21:29:b5:dc:7c [PTK=CCMP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:21:29:b5:dc:7c completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
netlink: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: Supplicant port status: Authorized
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick


```


and running dhclient on ra0 brings up the interface, looks like no problem there.  Let me try hibernating and waking up from this state, with network-manager not running, before that would trigger an oops...

...hmm, that seems to work with no problem.  Maybe network-manager is the culprit, let me try running without that for a while.

---

### Post by praseodym on 2011-12-23
Try Wicd instead:

```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
```
and remove the NM _completely_. Choose **ra0** as interface name and **wext** as driver.

---

### Post by kgoess on 2012-01-04
Ohh, that's great! It's all working again, after like two months of this!  Thank you!

I needed to do this to get the system tray icon though: [http://askubuntu.com/questions/69005/wicd-tray-icon-doesnt-show](http://askubuntu.com/questions/69005/wicd-tray-icon-doesnt-show)

What is up with network-manager causing kernel faults anyway?

---

### Post by kgoess on 2012-01-24
After further review, the ubuntu kernel update yesterday completely broke it, the rt3562sta driver causes a kernel oops whenever it's loaded (yes, after I recompiled for the new kernel).  So rather than wasting even more time on it  I just went out and bought a wifi AP and am using ethernet to connect to the AP, and let the AP deal with the wifi.  Wifi on linux truly sucks.

---

