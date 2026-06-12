---
title: "another wireless problem (wpa and centrino)"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by Eval on 2006-01-13
Hi everybody,

That's a long time that I try to setup my wpa connection, but I'have always blocked :(

I'have a ipw2200 and wpasupplicant on my notebook and without any encryption everything work fine :

*with ipw driver:*
I begin with the config file :
```

$ cat /etc/wpa_supplicant.conf2
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
#eapol_version=1
#Let wpa_supplication take care of scanning and AP selection
ap_scan=1
#fast_reauth=1

network={
        ssid="WANADOO-nico"
        key_mgmt=NONE
}

```

and I following by starting wpasupplicant :
```

$ sudo wpa_supplicant -w -i eth1 -c /etc/wpa_supplicant.conf2 -D ipw -d
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf2' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf2' -> '/etc/wpa_supplicant.conf2'
Reading configuration file '/etc/wpa_supplicant.conf2'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0 (from group name 'root')
ap_scan=1
Priority group 0
   id=0 ssid='WANADOO-nico'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:0e:35:80:fb:8f
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 455 bytes of scan results (2 BSSes)
Scan results: 2
..............

```

and I use dhcp for the IP adress :
```

$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 9563
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:80:fb:8f
Sending on   LPF/eth1/00:0e:35:80:fb:8f
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.11 -- renewal in 39816 seconds.

```

*and with wext driver :*
I've reset my network configuration :
```

$ sudo ifconfig eth1 down

```

start wpasupplicant :
```

$ sudo wpa_supplicant -w -i eth1 -c /etc/wpa_supplicant.conf2 -D wext
ioctl[SIOCSIWPMKSA]: Operation not supported
Trying to associate with 00:14:a4:58:03:b5 (SSID='WANADOO-nico' freq=0 MHz)
Associated with 00:14:a4:58:03:b5
CTRL-EVENT-CONNECTED - Connection to 00:14:a4:58:03:b5 completed (auth)
CTRL-EVENT-EAP-FAILURE EAP authentication failed
...................

```

and allocate an ip with dhcp :
```

$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:80:fb:8f
Sending on   LPF/eth1/00:0e:35:80:fb:8f
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.11 -- renewal in 33596 seconds.

```


So everything is good without encryption. But I'have already a question :
why I'have got all of this error messages with ipw driver? 
like : 
```

ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.

```

No I show you the main problem :

I try to set up the encryption (I'm using a livebox -the access point of the french ISP Wanadoo- so I'must using WPA/TKIP-PSK) :

I'm using an other configuration file :
```

$ cat /etc/wpa_supplicant.conf3
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="WANADOO-nico"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk="myKey"
}

```

and I try to start wpasupplicant with ipw driver:
```

$ sudo wpa_supplicant -w -i eth1 -c /etc/wpa_supplicant.conf3 -D ipw -d
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf3' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf3' -> '/etc/wpa_supplicant.conf3'
Reading configuration file '/etc/wpa_supplicant.conf3'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='WANADOO-nico'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:0e:35:80:fb:8f
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 712 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:14:a4:58:03:b5 (SSID='WANADOO-nico' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE

```

in the same time (like no encryption mode) I try to use dhcp but, this one don't establish the connection and finish by a timeout.

So I try without dhcp :
```

$ sudo ifconfig eth1 192.168.1.2 netmask 255.255.255.0
$ sudo route add default gw 192.168.1.1 dev eth1

```

```

$ sudo wpa_supplicant -w -i eth1 -c /etc/wpa_supplicant.conf3 -D ipw -d
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf3' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf3' -> '/etc/wpa_supplicant.conf3'
Reading configuration file '/etc/wpa_supplicant.conf3'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='WANADOO-nico'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:0e:35:80:fb:8f
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 516 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:14:a4:58:03:b5 (SSID='WANADOO-nico' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=21
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 514 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:14:a4:58:03:b5 (SSID='WANADOO-nico' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=21
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 516 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:14:a4:58:03:b5 (SSID='WANADOO-nico' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=21
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 3
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 515 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:14:a4:58:03:b5 (SSID='WANADOO-nico' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=21
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 4
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0

```

and I try o test my network with a ping command on the access point, but it's not working (network is unreachable).

So I try with the wext driver :
I have always my network configuration :
```

$ sudo route add default gw 192.168.1.1 dev eth1
$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
$ ifconfig eth1
eth1      Lien encap:Ethernet  HWaddr 00:0E:35:80:FB:8F  
          inet adr:192.168.1.2  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20e:35ff:fe80:fb8f/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:375 overruns:0 frame:0
          TX packets:3 errors:0 dropped:12 overruns:0 carrier:1
          collisions:0 lg file transmission:1000 
          RX bytes:692169 (675.9 KiB)  TX bytes:260576 (254.4 KiB)
          Interruption:4 Mémoire:ff9ee000-ff9eefff 


```

and I try to start wpasupplicant :
```

$ sudo wpa_supplicant -w -i eth1 -c /etc/wpa_supplicant.conf3 -D wext -d
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf3' driver 'wext'
Configuration file '/etc/wpa_supplicant.conf3' -> '/etc/wpa_supplicant.conf3'
Reading configuration file '/etc/wpa_supplicant.conf3'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='WANADOO-nico'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:0e:35:80:fb:8f
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:14:a4:58:03:b5
State: SCANNING -> ASSOCIATED
Associated to a new BSS: BSSID=00:14:a4:58:03:b5
No keys have been configured - skip key clearing
Network configuration found for the current AP
WPA: Failed to parse WPA IE from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Associated with 00:14:a4:58:03:b5
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Scan timeout - try to get results
Received 518 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Already associated with the selected AP.
Authentication with 00:14:a4:58:03:b5 timed out.
Added BSSID 00:14:a4:58:03:b5 into blacklist
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:14:a4:58:03:b5 blacklist count incremented to 2
State: SCANNING -> DISCONNECTED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Scan timeout - try to get results
Received 516 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - blacklisted
No APs found - clear blacklist and try again
Removed BSSID 00:14:a4:58:03:b5 from blacklist (clear)
Selecting BSS from priority group 0
0: 00:11:d8:1e:a4:8c ssid='WANADOO-6D78' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:14:a4:58:03:b5 ssid='WANADOO-nico' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:14:a4:58:03:b5 (SSID='WANADOO-nico' freq=0 MHz)
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
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=21
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:14:a4:58:03:b5
State: ASSOCIATING -> ASSOCIATED
Associated to a new BSS: BSSID=00:14:a4:58:03:b5
No keys have been configured - skip key clearing
Associated with 00:14:a4:58:03:b5
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:14:a4:58:03:b5
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:14:a4:58:03:b5 (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Renewed SNonce - hexdump(len=32): d2 69 66 03 54 85 19 9e d1 ab 0a c0 b3 3c 2d bb f3 54 51 4c 9c 44 de 6a 3a cc a1 93 9e 12 75 87
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:14:a4:58:03:b5
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:14:a4:58:03:b5 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:14:a4:58:03:b5
IEEE 802.1X RX: version=1 type=3 length=108
  EAPOL-Key type=254
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: RX message 1 of Group Key Handshake from 00:14:a4:58:03:b5 (ver=1)
WPA: Unsupported TKIP Group Cipher key length 13 (13).
RX EAPOL from 00:14:a4:58:03:b5
IEEE 802.1X RX: version=1 type=3 length=108
  EAPOL-Key type=254
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: RX message 1 of Group Key Handshake from 00:14:a4:58:03:b5 (ver=1)
WPA: Unsupported TKIP Group Cipher key length 13 (13).
RX EAPOL from 00:14:a4:58:03:b5
IEEE 802.1X RX: version=1 type=3 length=108
  EAPOL-Key type=254
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: RX message 1 of Group Key Handshake from 00:14:a4:58:03:b5 (ver=1)
WPA: Unsupported TKIP Group Cipher key length 13 (13).
RX EAPOL from 00:14:a4:58:03:b5
IEEE 802.1X RX: version=1 type=3 length=108
  EAPOL-Key type=254
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: RX message 1 of Group Key Handshake from 00:14:a4:58:03:b5 (ver=1)
WPA: Unsupported TKIP Group Cipher key length 13 (13).
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:14:a4:58:03:b5 into blacklist
State: GROUP_HANDSHAKE -> DISCONNECTED
EAPOL: External notification - portEnabled=0........

```


And for finish I try to ping,but I'have got the same answer : network unreachable...

I'm using the last ipw2200 driver : 1.0.10, firmware 2.4 and ieee80211 : 1.1.8

I create the config file for ipw2200 driver :
```

$ cat /etc/modprobe.d/ipw2200 
options ipw2200 led=1 hwcrypto=0

```

I try with different kernel (2.6.12 and 2.6.14.5) and I'have always no solution for my problem. Somebody have any idea please?

p.s. sorry for my english, I'have always create a post on the french forum but my problem still not solved...

---

### Post by Mr_Grieves on 2006-01-13
Reading from this thread.. this seems to be a kernel problem...
A person with a similar problem seems to solved the problem with using 2.6.11 kernel, though, that was slackware.

[http://www.linuxquestions.org/questions/showthread.php?t=365504](http://www.linuxquestions.org/questions/showthread.php?t=365504)

---

### Post by Eval on 2006-01-14
ok, and thanks for reply. I'm compiling the 2.6.11 kernel and test it :)

I just try to test it, but I've a problem to compile ieee80211 :
```

$ make
Checking in /lib/modules/2.6.11.12/build/ for ieee80211 components...
make -C /lib/modules/2.6.11.12/build M=/home/nico/wifi/ieee80211-1.1.8 MODVERDIR=/home/nico/wifi/ieee80211-1.1.8 modules
make[1]: entrant dans le répertoire « /usr/src/linux-2.6.11.12 »
  CC [M]  /home/nico/wifi/ieee80211-1.1.8/ieee80211_module.o
In file included from /home/nico/wifi/ieee80211-1.1.8/ieee80211_module.c:53:
/home/nico/wifi/ieee80211-1.1.8/net/ieee80211.h:1145: erreur: syntax error before 'flags'
/home/nico/wifi/ieee80211-1.1.8/net/ieee80211.h:1146: attention : function declaration isn't a prototype
/home/nico/wifi/ieee80211-1.1.8/net/ieee80211.h: In function 'kzalloc':
/home/nico/wifi/ieee80211-1.1.8/net/ieee80211.h:1147: erreur: 'size' undeclared (first use in this function)
/home/nico/wifi/ieee80211-1.1.8/net/ieee80211.h:1147: erreur: (Chaque identificateur non déclaré est rapporté une seule fois
/home/nico/wifi/ieee80211-1.1.8/net/ieee80211.h:1147: erreur: pour chaque fonction dans laquelle il apparaît.)
/home/nico/wifi/ieee80211-1.1.8/net/ieee80211.h:1147: erreur: 'flags' undeclared (first use in this function)
make[2]: *** [/home/nico/wifi/ieee80211-1.1.8/ieee80211_module.o] Erreur 1
make[1]: *** [_module_/home/nico/wifi/ieee80211-1.1.8] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-2.6.11.12 »
make: *** [modules] Erreur 2

```

I must compile the 2.6.11 kernel with gcc-3.3 (MAKEFLAGS="CC=gcc-3.3" make-kpkg --revision <my computer's name>.0 kernel_image), but I'm not sure of the command line to use the same version of gcc with make. All of my test have not result, anybody knows it or have any idea please?

---

