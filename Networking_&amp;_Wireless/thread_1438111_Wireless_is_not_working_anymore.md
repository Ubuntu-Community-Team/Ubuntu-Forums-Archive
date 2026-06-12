---
title: "Wireless is not working anymore"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by heksita on 2010-03-24
Hello all,

I have a problem with my wireless connection and I need some help with it :).

I have a D-LINK router with a wireless with a WPA2 (Personal). Couple of days ago I switched to Lucid Lynx 10.04. Wireless was working fine until one day it disconnected and never connected again.

Now, some facts:

1. I don't have any problems with wired connection.
2. My system is up-to-date.
3. My SSID is unique and visible.
4. Another computer with Fedora does not have any problem with this wireless.
5. My wireless card is switched on and I am able to connect to an unsecured network somewhere in my neighborhood (so my wifi card still works).
6. I rebooted my router several times, restored all settings to defaults and created a new wifi network.
7. I use DHCP on LAN.

System info:

```
uname -r
2.6.32-16-generic
```

```
lspci
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
```

lsmod indicates I have a ipw2200 module loaded.

```
iwlist eth1 auth
Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		Unknown
          Current Key management :
		Unknown
          Current Pairwise cipher :
		Unknown
          Current Pairwise cipher :
		Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : yes
          Current Privacy invoked : yes
```

```
lshw -C network
*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:72:63:9d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:11 memory:d0001000-d0001fff
```


Usually I use nm-applet. It tries to connect and then shows a prompt to type in a correct WPA password. I have a good one.
I changed my password -- still it cannot connect.
I changed to WEP. I turned it off and leave the network unprotected -- still the same.


I tried to connect via wpa_supplicant:

```
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     6c 69 6d 6d 61 74                                 limmat          
scan_ssid=1 (0x1)
proto: 0x2
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='limmat'
Interface eth1 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0e:35:72:63:9d
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 54 48 c9 bc ea 63 56 3f 86 50 26 e0 22 84 91 ac
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
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     6c 69 6d 6d 61 74                                 limmat          
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 2647 bytes of scan results (10 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:24:01:69:02:76 ssid='limmat' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:24:01:69:02:76 ssid='limmat'
Trying to associate with 00:24:01:69:02:76 (SSID='limmat' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b19 len=8
Received 2648 bytes of scan results (10 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:24:01:69:02:76 ssid='limmat' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:24:01:69:02:76 ssid='limmat'
Already associated with the selected AP.
RSN: Ignored PMKID candidate without preauth flag
EAPOL: disable timer tick
Authentication with 00:24:01:69:02:76 timed out.
Added BSSID 00:24:01:69:02:76 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
```

And so on, and so on.

I tried connecting with wicd -- it tells me that there is an authentication failure.

With WPA turned off I tried to connect manually:

```
sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:0e:35:72:63:9d
Sending on   LPF/eth1/00:0e:35:72:63:9d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I even tried a manual IP configuration. Still -- without any success.

This might me similar to [this thread]("http://ubuntuforums.org/showthread.php?t=1433155"), but I cannot connect to wifi at all, no matter if it is WPA or WEP (or nothing). I would suspect that this is a problem with my router, but as I mentioned above, I have a second computer which has no problems with this particular wireless connection.

Any ideas? Wired connection is not very comfortable...

---

