---
title: "Wireless connection on Acer Aspire One - CLI"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by Mercedes300 on 2010-02-06
Hi there,

I am trying to ditch my GUI and go all CLI, so I'm trying to setup a connection to my wireless router (preferably static IP'ed so I can use NFS) and am having some trouble.

Let me just say right off the bat, if anyone knows an application for CLI that handles this stuff like nm-applet for gnome, that would be great!

Following several guides I've tried the following (all as root):

```

ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 192.168.125.98 netmask 255.255.255.0 up
route add default gw 192.168.125.1
iwconfig wlan0 essid myessid key s:mykey

```

Running the commands fails at the last command with 
```
Error for wireless request "Set Encode" (8B2A) :
SET failed on device wlan0 ; Invalid argument.
```

From googling, I think this might have something to do with the driver, however I'm able to connect with this driver using nm-applet... 

Any help would be great, even if it's sending me in a whole new direction. :)

---

### Post by Mercedes300 on 2010-02-06
Ok, got an update

Following this guide [HERE]("http://ubuntuforums.org/showthread.php?t=571188")

Worked like a charm... the first time. I then decided to see if I could get it on boot with /etc/rc.local .

```
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 192.168.125.98 netmask 255.255.255.0 up
route add default gw 192.168.125.1
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
```

After placing the same commands I ran to get it to go the first time (see above) in /etc/rc.local, and a reboot, the interface was up, but couldn't ping the router.

So I ran the last command myself to see the output. It reported that there was a file in /var/run/wpa_supplicant that was saying another instance of the program was running, or it should be removed because it was there from a bad shut-down.

So after killing all instances of wpa_supplicant, the "lock" file went away (it was a "socket" file-type?) So I commented out the rc.local file and rebooted.

So, one more try at this full list of commands typed in one by one to see output. Everything went good till the last command where it complained about not being able to see any access points and seemed to be in a loop.
```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=8):
     7a 69 70 70 6f 6e 65 74                           zipponet        
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='zipponet'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:23:4e:57:04:00
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 62 54 29 ca ab c9 5e ab 9b 9a cb af 8d 5d 06 58
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
Ignore event for foreign ifindex 3
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Cached scan results are empty - not posting
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: disable timer tick
Scan timeout - try to get results
Received 1090 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS-AP-AVAILABLE 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:df:a9:31:d3 ssid='ZIPPO_AP1' wpa_ie_len=28 rsn_ie_len=24 caps=0x10
   skip - SSID mismatch
1: 00:1c:df:7f:36:07 ssid='zipponet' wpa_ie_len=28 rsn_ie_len=24 caps=0x10
   selected based on WPA IE
   selected WPA AP 00:1c:df:7f:36:07 ssid='zipponet'
Trying to associate with 00:1c:df:7f:36:07 (SSID='zipponet' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 02 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c02 len=191
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE0c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIE183060dd07000c4304000000)'
Association info event
req_ies - hexdump(len=50): 00 08 7a 69 70 70 6f 6e 65 74 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=28): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 07 00 0c 43 04 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:df:7f:36:07
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1c:df:7f:36:07 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
Scan timeout - try to get results
Received 1218 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS-AP-AVAILABLE 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:df:a9:31:d3 ssid='ZIPPO_AP1' wpa_ie_len=28 rsn_ie_len=24 caps=0x10
   skip - SSID mismatch
1: 00:1c:df:7f:36:07 ssid='zipponet' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1c:df:7f:36:07 ssid='zipponet'
Trying to associate with 00:1c:df:7f:36:07 (SSID='zipponet' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 02 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c02 len=191
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE0c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIE183060dd07000c4304000000)'
Association info event
req_ies - hexdump(len=50): 00 08 7a 69 70 70 6f 6e 65 74 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=28): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 07 00 0c 43 04 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:df:7f:36:07
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
BSSID 00:1c:df:7f:36:07 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
Scan timeout - try to get results
Received 1218 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS: attr type=0x1041 len=1
WPS: attr type=0x103b len=1
WPS: attr type=0x1047 len=16
WPS: attr type=0x1021 len=18
WPS: attr type=0x1023 len=17
WPS: attr type=0x1024 len=7
WPS: attr type=0x1042 len=14
WPS: attr type=0x1054 len=8
WPS: attr type=0x1011 len=27
WPS: attr type=0x1008 len=2
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS: attr type=0x1041 len=1
WPS: attr type=0x103b len=1
WPS: attr type=0x1047 len=16
WPS: attr type=0x1021 len=18
WPS: attr type=0x1023 len=17
WPS: attr type=0x1024 len=7
WPS: attr type=0x1042 len=14
WPS: attr type=0x1054 len=8
WPS: attr type=0x1011 len=27
WPS: attr type=0x1008 len=2
WPS-AP-AVAILABLE 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:df:7f:36:07 ssid='zipponet' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - blacklisted
1: 00:1c:df:a9:31:d3 ssid='ZIPPO_AP1' wpa_ie_len=28 rsn_ie_len=24 caps=0x10
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1c:df:7f:36:07 ssid='zipponet' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - blacklisted
1: 00:1c:df:a9:31:d3 ssid='ZIPPO_AP1' wpa_ie_len=28 rsn_ie_len=24 caps=0x10
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:1c:df:7f:36:07 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:df:7f:36:07 ssid='zipponet' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1c:df:7f:36:07 ssid='zipponet'
Trying to associate with 00:1c:df:7f:36:07 (SSID='zipponet' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 02 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c02 len=191
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE0c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIE183060dd07000c4304000000)'
Association info event
req_ies - hexdump(len=50): 00 08 7a 69 70 70 6f 6e 65 74 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=28): 01 08 82 84 8b 96 12 24 48 6c 2a 01 04 32 04 0c 18 30 60 dd 07 00 0c 43 04 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:df:7f:36:07
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:df:7f:36:07
No keys have been configured - skip key clearing
Associated with 00:1c:df:7f:36:07
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1c:df:7f:36:07 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Removed BSSID 00:1c:df:7f:36:07 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
```


So another reboot. Checked that the interface was up, with no IP address or nothing (obviosly). I then ran ```
iwlist wlan0 scan
``` and it reported:
```
wlan0   No scan results
```
and also:
```
wlan0     Interface doesn't support scanning : Device or resource busy
```

So to sum up where I am:

I have no idea why it worked the first time and now it doesn't work.

It seems to be getting worse. Even though I'm only enter the same commands that worked the first time.

Any ideas?

Sorry for the long post, just trying to be thorough.

---

### Post by Mercedes300 on 2010-02-06
Thought I would through my wpa_supplicant.conf file up here as well.

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="zipponet"
	scan_ssid=0
	proto=WPA
	key_mgmt=WPA-PSK
	psk="n4bdrki4dos"
	pairwise=TKIP
	group=TKIP
}

```

P.S. this is hour 4!

---

