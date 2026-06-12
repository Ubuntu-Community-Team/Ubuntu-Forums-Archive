---
title: "WEP not working on IBM T30 laptop"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by pgavin on 2006-06-21
Hello,

I've got an IBM T30 laptop, which has a Cisco AiroNet 350 Mini-PCI card.  Using NetworkManager, I am able to connect to an unsecured wireless network, but I'm not able to connect to one using any kind of WEP.  Everything worked fine in hoary, but as soon as I upgraded to dapper, I was unable to get it to connect.

It looks like the module loads up OK:

```

pgavin@crm-114:~$ dmesg|grep airo
[17179594.900000] airo:  Probing for PCI adapters
[17179595.272000] airo: Found an MPI350 card
[17179596.312000] airo: MAC enabled eth0 0:2:8a:31:b3:45
[17179596.312000] airo:  Finished probing for PCI adapters

```

This is what gets dumped to /var/log/daemon.log when I switch to an AP using WEP:

```

Jun 21 09:42:06 localhost NetworkManager: <information>^Imatch 
Jun 21 09:42:06 localhost NetworkManager: <debug info>^I[1150897326.793870] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'accesspoint' 
Jun 21 09:42:06 localhost NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth0 / accesspoint 
Jun 21 09:42:06 localhost NetworkManager: <information>^IDeactivating device eth0. 
Jun 21 09:42:06 localhost dhclient: wifi0: unknown hardware address type 801
Jun 21 09:42:06 localhost dhclient: wifi0: unknown hardware address type 801
Jun 21 09:42:06 localhost dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jun 21 09:42:09 localhost NetworkManager: <information>^IDevice eth0 activation scheduled... 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) started... 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jun 21 09:42:09 localhost NetworkManager: <information>^Imatch 
Jun 21 09:42:09 localhost NetworkManager: <information>^Imatch 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0/wireless): access point 'accesspoint' is encrypted, but NO valid key exists.  New key needed. 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) New wireless user key requested for network 'accesspoint'. 
Jun 21 09:42:09 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jun 21 09:42:09 localhost NetworkManager: <information>^Imatch 
Jun 21 09:42:10 localhost last message repeated 15 times
Jun 21 09:42:36 localhost NetworkManager: <information>^IActivation (eth0) New wireless user key for network 'accesspoint' received. 
Jun 21 09:42:36 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 21 09:42:36 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jun 21 09:42:36 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 21 09:42:36 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jun 21 09:42:36 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jun 21 09:42:36 localhost NetworkManager: <information>^IActivation (eth0/wireless): access point 'accesspoint' is encrypted, and a key exists.  No new key needed. 
Jun 21 09:42:37 localhost NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth0^I^Iwext^I/var/run/wpa_supplicant^I' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was '0' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 546865204279746573686f70' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Jun 21 09:42:38 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jun 21 09:42:38 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Global control interface '/var/run/wpa_supplicant-global' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX global ctrl_iface - hexdump_ascii(len=49): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      68 30 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h0__wext_/var/ru 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      09                                                _                
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth0^I^Iwext^I/var/run/wpa_supplicant^I' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Initializing interface 'eth0' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Initializing interface (2) 'eth0' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): EAPOL: SUPP_PAE entering state DISCONNECTED 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): EAPOL: SUPP_BE entering state INITIALIZE 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): EAP: EAP entering state DISABLED 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): EAPOL: External notification - portEnabled=0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): EAPOL: External notification - portValid=0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): SIOCGIWRANGE: WE(compiled)=19 WE(source)=12 enc_capa=0x0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):   capabilities: key_mgmt 0x0 enc 0x3 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Own MAC address: 00:02:8a:31:b3:45 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wpa_driver_wext_set_wpa 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):  
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wpa_driver_wext_set_countermeasures 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wpa_driver_wext_set_drop_unencrypted 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Setting scan request: 0 sec 100000 usec 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Added interface eth0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Wireless event: cmd=0x8b06 len=8 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX ctrl_iface - hexdump_ascii(len=9): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Wireless event: cmd=0x8b2a len=8 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX ctrl_iface - hexdump_ascii(len=11): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE: ADD_NETWORK 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Wireless event: cmd=0x8b2a len=8 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): hexdump_ascii(len=43): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      69 64 20 35 34 36 38 36 35 32 30 34 32 37 39 37   id 5468652042797 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      34 36 35 37 33 36 38 36 66 37 30                  46573686f70      
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='546865204279746573686f70' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): ssid - hexdump_ascii(len=12): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      54 68 65 20 42 79 74 65 73 68 6f 70               accesspoint     
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Wireless event: cmd=0x8b2a len=8 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX ctrl_iface - hexdump_ascii(len=27): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      79 5f 6d 67 6d 74 20 4e 4f 4e 45                  y_mgmt NONE      
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='NONE' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): key_mgmt: 0x4 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Wireless event: cmd=0x8b2a len=8 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX ctrl_iface - hexdump_ascii(len=33): [REMOVED] 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE: SET_NETWORK id=0 name='wep_key0' value='[REMOVED]' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wep_key0 - hexdump(len=5): [REMOVED] 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX ctrl_iface - hexdump_ascii(len=29): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 77 65   SET_NETWORK 0 we 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): 9 69 64 78 20 30            p_tx_keyidx 0    
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE: SET_NETWORK id=0 name='wep_tx_keyidx' value='0' 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): wep_tx_keyidx=0 (0x0) 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX ctrl_iface - hexdump_ascii(len=16): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE: ENABLE_NETWORK id=0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Setting scan request: 0 sec 0 usec 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): State: DISCONNECTED -> SCANNING 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Starting AP scan (broadcast SSID) 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): RX ctrl_iface - hexdump_ascii(len=6): 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):      41 54 54 41 43 48                                 ATTACH           
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): CTRL_IFACE monitor attached - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 31 33 39 2d 31 35 00 00 00 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Wireless event: cmd=0x8b19 len=8 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Received 442 bytes of scan results (3 BSSes) 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Scan results: 3 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): Selecting BSS from priority group 0 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): 0: 00:14:bf:f8:be:d0 ssid='accesspoint' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):    skip - no WPA/RSN IE 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344): 1: 00:0f:66:f3:48:15 ssid='linksysRf34815' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jun 21 09:42:38 localhost NetworkManager: <information>^Iwpa_supplicant(7344):    skip - no WPA/RSN IE 
Jun 21 09:42:39 localhost NetworkManager: <information>^IActivation (eth0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'accesspoint'. 
Jun 21 09:42:39 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 21 09:42:39 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jun 21 09:42:40 localhost NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Jun 21 09:42:40 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jun 21 09:42:40 localhost dhclient: wifi0: unknown hardware address type 801
Jun 21 09:42:40 localhost NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Jun 21 09:42:41 localhost NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Jun 21 09:42:41 localhost dhclient: wifi0: unknown hardware address type 801
Jun 21 09:42:44 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jun 21 09:42:52 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jun 21 09:43:05 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Jun 21 09:43:25 localhost NetworkManager: <information>^IDevice 'eth0' DHCP transaction took too long (>45s), stopping it. 
Jun 21 09:43:25 localhost dhclient: wifi0: unknown hardware address type 801
Jun 21 09:43:25 localhost dhclient: wifi0: unknown hardware address type 801
Jun 21 09:43:25 localhost dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jun 21 09:43:25 localhost dhclient: send_packet: Network is unreachable
Jun 21 09:43:25 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Jun 21 09:43:26 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jun 21 09:43:26 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Jun 21 09:43:26 localhost NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface eth0 
Jun 21 09:43:26 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Jun 21 09:43:26 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Jun 21 09:43:26 localhost NetworkManager: <debug info>^I[1150897406.444143] real_act_stage4_ip_config_timeout (): Activation (eth0/wireless): could not get IP configuration info for 'accesspoint', asking for new key. 
Jun 21 09:43:26 localhost NetworkManager: <information>^IActivation (eth0) New wireless user key requested for network 'accesspoint'. 
Jun 21 09:43:26 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 

```

At this point it gives up and asks me for a new key, although it looks like (for some reason) DHCP is failing.

If I turn off NetworkManager and set my /etc/network/interfaces like so:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp
wireless-essid accesspoint
wireless-key [my-wep-key]

```

and run ifup, I get this:

```

pgavin@crm-114:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:02:8a:31:b3:45
Sending on   LPF/eth0/00:02:8a:31:b3:45
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

However, if I use a non-WEP access point, everything works fine:

```

pgavin@crm-114:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:02:8a:31:b3:45
Sending on   LPF/eth0/00:02:8a:31:b3:45
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.113 -- renewal in 41712 seconds.

```

I've heard of a few other people having problems with this card as well, and I'm starting to think there may be a problem with the kernel driver.  Does anyone have any advice for me?

Pete

---

### Post by jml on 2006-06-21
one suggestion is to blacklist the kernal driver, sorry I don't know the exact details on how to do this, then use NDISWRAPPER to load the windows driver for the card.  That might work.

---

### Post by pgavin on 2006-06-21
Well, in any case, I found an Intel PRO/Wireless 2200 card lying around, so I swapped it out.  Now I have 802.11g, and it works like a charm :)

I'm pretty sure now that there's just a problem in the airo.c driver in dapper, though.

Pete

---

### Post by VortexICS on 2006-07-09
I have the same T30 and my Cisco Aironet 350 Mini-PCI was working fine for a month or so, up until yesterday, when I started experiencing the same problem with WEP on my Linksys54GS. I can connect through Windows with WEP, but under Dapper, only unsecured seem to work now. I have not changed anything in the configurations or performed a recent upgrade.  
I tried researching this forum but no concrete fix has been issued, so I guess I will try to get another card.

---

### Post by MerZo on 2006-07-28
I have the same problem on a Thinkpad R40. Including the Aironet Cisco card.

I can connect to a network without WEP, but when I try to connect to a WEP secured router it does not work.

The strange thing with this is that it has worked before, and suddenly just stopped as described in the other posters problem.

Can someone with good network experience please enlight this problem and try to solve this with us, because it is real annoying. I don't know where to look anymore, feels like I tried everything.

---

