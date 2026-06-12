---
title: "WPA2 wireless won't connect with Netgear USB Wireless stick"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by azenz on 2011-10-14
I installed my external Netgear WG111v2 USB wireless card to my Desktop running Ubuntu 10.04 64 bit using these commands:

sudo ndiswrapper -i netwg111.inf
[ndiswrapper -l outputs:  netwg111 : driver installed]
sudo modprobe ndiswrapper 

iwconfig output:

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Then I tried to connect to my WPA2 home network using the WiCD network manager. The manager finds my SSID and tries to connect, but eventually fails stating an authentication error. But I checked the password multiple times, and our Windows 7 laptop can connect using the same password. (WiCD connects using cable without problems). 

Then I tried wpa_supplicant, config file as follows:

network={
        ssid="FRITZ!Box Fon WLAN xxxx"
	scan_ssid=1
        key_mgmt=WPA-PSK
        psk="xxxxxxxxxxxxxxxx" (16 numbers)
}

(I assume the password won't need conversion into HEX, in any case I tried it but it complained that it exceeded 63 characters.)

Then I ran: sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -d


OUTPUT is:

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='FRITZ!Box Fon WLAN 7112'
Initializing interface (2) 'wlan0'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1e:2a:ec:6b:65
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 06 55 e1 6f 7d 7b 58 46 a5 47 89 f4 1b d3 0d 45
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=16
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=23):
     46 52 49 54 5a 21 42 6f 78 20 46 6f 6e 20 57 4c   FRITZ!Box Fon WL
     41 4e 20 37 31 31 32                              AN 7112         
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1173 bytes of scan results (2 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: bc:05:43:33:7a:96 ssid='FRITZ!Box Fon WLAN 7112' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP bc:05:43:33:7a:96 ssid='FRITZ!Box Fon WLAN 7112'
Trying to associate with bc:05:43:33:7a:96 (SSID='FRITZ!Box Fon WLAN 7112' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 16 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
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
Wireless event: cmd=0x8b1a len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=39
EAPOL: disable timer tick
Authentication with bc:05:43:33:7a:96 timed out.
Added BSSID bc:05:43:33:7a:96 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING


And that goes on and on. 

Your HELP would be greatly appreciated. I had previously been able to use this Netgear with an older Ubuntu version, I think 8.10 or 9.04, without problems. Now I have a different wireless system and a newer Ubuntu.

---

