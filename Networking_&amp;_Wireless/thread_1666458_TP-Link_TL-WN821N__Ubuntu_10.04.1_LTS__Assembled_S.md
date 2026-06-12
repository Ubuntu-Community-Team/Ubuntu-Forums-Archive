---
title: "TP-Link TL-WN821N / Ubuntu 10.04.1 LTS / Assembled Server"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by min_max9000 on 2011-01-13
TP-Link TL-WN821N / Ubuntu 10.04.1 LTS / Assembled Server

I am trying to get my server onto the the network wirelessly and failing misserably. I am piped in over ssh through eth0, and cannot configure wlan0.

This is my current /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet dhcp

# secondary network interface
auto eth0
iface eth0 inet dhcp

```

This is my current wpa_supplicant.conf:
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="Apple Network 2ae2d4"
scan_ssid=0
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
#psk="XXXXXXXXXXX"
psk=dee5c2f18b0ba5d655fdb28fef21bcc4f24306edb1affdf1984338ce16900985
}

```

Upon executing this:
```
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
```

I get this:
```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=20):
     41 70 70 6c 65 20 4e 65 74 77 6f 72 6b 20 32 61   Apple Network 2a
     65 32 64 34                                       e2d4            
scan_ssid=0 (0x0)
proto: 0x2
key_mgmt: 0x2
pairwise: 0x10
group: 0x10
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Apple Network 2ae2d4'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: d8:5d:4c:8a:d9:1c
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): b8 ed f7 63 7d 23 56 e1 ae fb 48 40 84 53 c1 d9
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
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
```

And it continually fails to authenticate. Below are all the detail:

1 ) Machine Brand and Model (PC/Laptop):
- assembled server

2 ) Wireless Brand, Model and Wireless Chipset:
- TP-Link TL-WN821N
- Bus 001 Device 002: ID 0cf3:1002 Atheros Communications, Inc.

3 ) check interface:

wlan0     Link encap:Ethernet  HWaddr d8:5d:4c:8a:d9:1c  
		BROADCAST MULTICAST  MTU:1500  Metric:1
		RX packets:23 errors:0 dropped:0 overruns:0 frame:0
		TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000 
		RX bytes:3754 (3.7 KB)  TX bytes:3414 (3.4 KB)



wlan0     IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


4 ) Check for modules:
- none for wireless

5 ) Kernel boot messages

[ 1116.539128] wlan0: associate with AP 00:1b:63:2a:e2:d4 (try 1)
[ 1116.541738] wlan0: RX AssocResp from 00:1b:63:2a:e2:d4 (capab=0x431 status=0 aid=2)
[ 1116.541743] wlan0: associated
[ 1116.547352] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1127.470028] wlan0: no IPv6 routers present
[ 1133.032489] wlan0: deauthenticating from 00:1b:63:2a:e2:d4 by local choice (reason=3)
[ 1215.327991] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4735.292298] usb 1-1: kill pending tx urbs.


6 ) Network configuration

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: d8:5d:4c:8a:d9:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.1.5 multicast=yes wireless=IEEE 802.11bg

7 ) Scan for networks:
- wlan0     No scan results

8 ) Ubuntu 10.04.1 LTS

9 ) Kernel/architecture (including 32 vs. 64 bit): 
- 2.6.32-27-server x86_64

---

