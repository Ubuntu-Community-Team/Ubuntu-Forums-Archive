---
title: "Dlink wlan connection with ndiswrapper; essid not accepted: help needed"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by blesbok on 2010-05-10
wlan connection with ndiswrapper, pcmcia; essid not accepted: help needed

My wlan worked like a bomb... before the upgrade to kernel 2.6.31-14.  A failure to get some avahi package may have been part of the cause.  Now I can't see my ESSID and AP using iwconfig wlan0.  This can possibly be bypassed using WPA_supplicant but it seems that's only for an encrypted connection; I'm trying to join an unencrypted network.  It's the output of the command
 sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext
that seems to tell me I'm close:

Try to find WPA-enabled AP
0: 00:0c:42:31:99:e1 ssid='Bittserv' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:0c:42:31:99:e1 ssid='Bittserv' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - non-WPA network not allowed

It's after weeks of searching and trying things that I approach this forum.  An obvious solution would be to reinstall Linux-Mint Helena from CD-- but how would I upgrade thereafter?

Here are some clues:
the wireless card: D-Link G520 with Atheros AR5001X chipset

sudo iwlist scan
...
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:42:31:66:E1
                    ESSID:"Bittserv"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:2 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sudo iwconfig wlan0

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



sudo ndiswrapper -l

		neta3ab : driver installed
			device (168C:0013) present (alternate driver: ath5k)



cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto wlan0

iface wlan0 inet dhcp
wireless-essid Bittserv
mode managed
wpa-ssid default
wpa-ap-scan 1
/sbin/wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
address 10.92.93.1
netmask 255.255.255.0
gateway 192.168.1.1

 

cat /etc/wpa_supplicant.conf

 sudo cat /etc/wpa_supplicant.conf 
#network={
#	ssid="Bittserv"
#}
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
	ssid="Bittserv"
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP
	scan_ssid=1
	psk="pa55word"



output of sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='0'
eapol_version=1
ap_scan=1
fast_reauth=1
Priority group 0
   id=0 ssid='Bittserv'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1b:11:b0:56:cf
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): c3 12 48 b9 d9 bb 59 40 18 f3 ef 2f 65 78 ba ef
...
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
ctrl_interface_group=0
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=8):
     5a 69 70 70 62 65 72 67                           Bittserv        
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 137 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:0c:42:31:99:e1 ssid='Bittserv' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:0c:42:31:66:e1 ssid='Bittserv' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - non-WPA network not allowed
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick



sudo pppoe-discovery -I wlan0

Timeout waiting for PADO packets

Thank you for reading.  Will greatly appreciate any advice. [http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

---

### Post by blesbok on 2010-05-28
This card almost works with the ath5k driver instead of ndiswrapper.  It seems wpa_supplicant causes the same Access Point problem (here essid accepted but not ap), but if you don't need WPA, it worked for me when I deleted (after backup) /etc/dbus-1/system.d/wpa_supplicant.conf  After an upgrade, the problem resurfaced but a temporary removal of avahi.conf in the same directory got things back to normal.

[http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

---

