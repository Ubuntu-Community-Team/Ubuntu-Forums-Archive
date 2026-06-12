---
title: "annoying WPA configuration"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by ffffxxxx on 2006-07-09
hello
i try the guide from
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA](http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA)
i am using ndiswrapper
and  my /etc/wpa_supplicant.conf
-----
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="my ssid"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="my password"
}
-----
i am using wpa pre-share key

but i got the following message

--Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=5):
     77 65 66 65 77                                    wefew
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='wefew'
Initializing interface (2) 'wlan0'
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0x5
  capabilities: key_mgmt 0x5 enc 0x7
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:40:f4:e1:5b:72
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 479 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:12:17:bc:12:6d ssid='wefew' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:12:17:bc:12:6d (SSID='wefew' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:12:17:bc:12:6d into blacklist
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 479 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:12:17:bc:12:6d ssid='wefew' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:12:17:bc:12:6d (SSID='wefew' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:12:17:bc:12:6d blacklist count incremented to 2
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
-----


i also install network manager but its not very useful
what should i do?
thanks

---

### Post by ffffxxxx on 2006-07-09
someone please help?

---

### Post by slakkie on 2006-07-09
> **ffffxxxx said:**
> hello
i try the guide from
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA](http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA)
i am using ndiswrapper
and  my /etc/wpa_supplicant.conf
-----
[snip, wpa logs]
-----

i also install network manager but its not very useful
what should i do?
thanks

I did it like this:
[http://www.ubuntuforums.org/showpost.php?p=1100808&postcount=194](http://www.ubuntuforums.org/showpost.php?p=1100808&postcount=194)

There are two possible problems that you need to look at:
1) How did you create your password?
2) Startup WPA supplicant with the ndiswrapper driver. I use wext, you should use: ndiswrapper.

Hope this helps.

---

