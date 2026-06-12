---
title: "Orange Livebox Wifi"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by ZootHornRollo on 2011-01-16
Hi,

From reading it appears that this has been a problem for others but i cannot seem to get mine connected.

I have followed a couple of online guides and still cannot connect.  This is the one i am using now [http://tinycorelinux.com/forum/index.php?topic=4394.0](http://tinycorelinux.com/forum/index.php?topic=4394.0)

My /etc/wpa_supplicant.conf 

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="Livebox-C558"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=23db8869a6.................}
```

i get this output when running the command #sudo wpa_supplicant -Bdd -Dwext -i wlan0 -c/etc/wpa_configure.conf#:

```
graham@musicbox:~$ sudo wpa_supplicant -Bdd -Dwext -i wlan0 -c/etc/wpa_configure.conf
Initializing interface 'wlan0' conf '/etc/wpa_configure.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_configure.conf' -> '/etc/wpa_configure.conf'
Reading configuration file '/etc/wpa_configure.conf'
Failed to read or parse configuration '/etc/wpa_configure.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout

```

Any help to resolve would be appreciated.  I have a copy of XP i can use that i am told will connect as easy as pie but i don't want to revert to that pish!

---

### Post by ZootHornRollo on 2011-01-16
jut noticed my effing stupid mistake!  i edited my wpa_supplicant file not the wpa_configure.

Now get this output :

```
graham@musicbox:~$ sudo wpa_supplicant -Bdd -Dwext -i wlan0 -c/etc/wpa_configure.conf
Initializing interface 'wlan0' conf '/etc/wpa_configure.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_configure.conf' -> '/etc/wpa_configure.conf'
Reading configuration file '/etc/wpa_configure.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=12):
     4c 69 76 65 62 6f 78 2d 43 35 35 38               Livebox-C558    
scan_ssid=0 (0x0)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Livebox-C558'
Initializing interface (2) 'wlan0'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0e:2e:45:42:fb
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 61 4e 57 05 6c 3f 52 11 83 b0 3a 29 82 37 db 63
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
Using existing control interface directory.
Added interface wlan0
Daemonize..
```

...but still cannot connect.

```
graham@musicbox:~$ sudo udhcpc -b -i wlan0
sudo: udhcpc: command not found

```

---

### Post by ZootHornRollo on 2011-01-18
still having no luck with this.  can anyone assist?

---

