---
title: "Need help with Dlink DWA-131 on Ubuntu 11.04 (Natty) [Driver r8712u]"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by selepo2 on 2011-08-01
Hi, I am a Linux noob but a quick learner and is currently struggling with a usb wifi dongle D-Link DWA-131. As I understand it it should have support in Natty based on the r8712u driver included in the kernel. I can't get it wo work however. My experience is that I can't access any encrypted Access Points, using an open network it seems to connect but is probably not stable since it keeps logging to syslog even when connected. 

It seems that there is some sort of timeout half way through the handshake. Have anyone else got this to to work with the same driver ? Any suggestions for troubleshooting ?

/Selepo2

Pasting the logs below
-----
user@host:/var/run$ lsusb | grep D-Link
Bus 001 Device 002: ID 07d1:3303 D-Link System

user@host:/var/run$ lsmod | grep r8712u
r8712u                307592  0

etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules

# The secondary network interface
auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

/etc/wpa_supplicant/wpa_supplicant.conf
#*wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
        ssid="HomeAP"
        id_str="HomeAP"
        priority=5
        key_mgmt=WPA-PSK
        psk="XXXXXXXXXXXXXXXXXX"
}

And*when*I*try*to*connect...

user@server:/var/run$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -d 

Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 5
   id=0 ssid='HomeAP'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: xx:xx:xx:xx:xx:xx
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): xx*xx*xx*xx*xx*xx*xx*xx*xx*xx*xx*xx*xx
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=48
State: DISCONNECTED -> SCANNING
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
EAPOL: Supplicant port status: Unauthorized
Scan timeout - try to get results
Received 587 bytes of scan results (2 BSSes)
BSS: Start scan result update 1
BSS: Add new id 0 BSSID 00:00:00:01:01:01 SSID 'HomeAP'
BSS: Add new id 1 BSSID 00:00:00:02:02:02 SSID 'HomeAP2'
New scan results available
Selecting BSS from priority group 5
Try to find WPA-enabled AP
0: 00:00:00:01:01:01 ssid='HomeAP' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:00:00:01:01:01 ssid='HomeAP'
Trying to associate with 00:00:00:01:01:01 (SSID='HomeAP' freq=2462 MHz)
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=26): xx*xx*xx*xx*xx*xx*xx*xx*xx
WPA: set AP RSN IE - hexdump(len=22):*xx*xx*xx*xx*xx*xx*xx*xx*xx
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): xx*xx*xx*xx*xx*xx*xx
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP fail=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portControl=Auto
EAPOL: Supplicant port status: Unauthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=23
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:01:01:01
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:00:00:01:01:01
No keys have been configured - skip key clearing
Associated with 00:00:00:01:01:01
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized

---

