---
title: "Atheros WPA2 woes"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by duibhceK on 2010-10-07
hi all, 
I'm having some problems getting WPA2 working on my desktop PC. I've tried a couple of solutions mentioned in threads on here and googled around as well, but i'm sort of stuck now.

I have 2 pcs with an atheros chipset, both using the ath5k driver:
laptop: AR5001 Wireless Network Adapter (rev 01)
desktop: AR5001X+ Wireless Network Adapter (rev 01)

everything works fine on the laptop. I'm using knetworkmanager without problem and it suffices for my laptop needs since I don't need network at boot time and the router is set to broadcast the SSID.

the desktop is a different story though. knetworkmanager does not want to connect using WPA2, it keeps asking me for the passphrase which I have checked and confirmed to be correct. Since I do want network at boot time on the machine I then tried to get things working by editing /etc/networking/interfaces and using wpa_supplicant. But to no avail. Using WEP does work ok, but I'd really prefer WPA2.

/etc/networking/interfaces now looks like this:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-essid MAGI
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my key in HEX>

```

/etc/wpa_supplicant.conf looks like this:
```

network={
  ssid="MAGI"
  scan_ssid=1
  pairwise=CCMP
  group=CCMP
  key_mgmt=WPA_PSK
  psk=<my key in HEX>
}

```

when I bring up wlan0 (with ifup) there's no obvious errors, but I do not get a DHCP lease.

So I manually tried running wpa_supplicant:
```
# wpa_supplicant -D wext -i wlan0 -c /etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='DIR=/var/run/wpa_supplicant'
Line: 6 - start of a new network block
ssid - hexdump_ascii(len=4):
     4d 41 47 49                                       MAGI            
scan_ssid=1 (0x1)
pairwise: 0x10
group: 0x10
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='MAGI'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:11:95:91:f7:47
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): ce 95 4c a3 be 6c 55 2b bc dd 58 43 91 e9 cc d7
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
Wireless event: cmd=0x8b19 len=16
Received 1162 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:bf:de:7a:6d ssid='MAGI' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:14:bf:de:7a:6d ssid='MAGI'
Trying to associate with 00:14:bf:de:7a:6d (SSID='MAGI' freq=2452 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=16
EAPOL: disable timer tick
Authentication with 00:14:bf:de:7a:6d timed out.
Added BSSID 00:14:bf:de:7a:6d into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     4d 41 47 49                                       MAGI            
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Cached scan results are empty - not posting
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No APs found - clear blacklist and try again
Removed BSSID 00:14:bf:de:7a:6d from blacklist (clear)

```

and it just goes on trying after that.

I could really use some help...

---

### Post by duibhceK on 2010-10-14
I still haven't been able to get this working. 

no-one has any ideas?

---

