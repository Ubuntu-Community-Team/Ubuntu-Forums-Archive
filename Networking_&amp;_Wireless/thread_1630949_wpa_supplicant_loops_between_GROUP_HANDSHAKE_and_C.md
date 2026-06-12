---
title: "wpa_supplicant loops between GROUP_HANDSHAKE and COMPLETED: Intel Wifi 5100 &amp; Belkin"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by SamStephens on 2010-11-25
EDIT 6 Dec: More detailed log from wpa_supplicant

I'm using Ubuntu Studio 10.10 x64. I want to get wireless networking going manually. My wireless networking works successfully in Windows 7 x64.

I can get it working successfully without encryption but when I try and use WPA-PSK, wpa_supplicant gets stuck in a loop between GROUP_HANDSHAKE and COMPLETED, as shown in the log below.

I've been working mostly off the instructions in this post: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

My laptop is a Dell Studio 1537. It has an Intel Wifi 5100. I'm connecting to a F5D7633-4 router running F5D7633-4Av1_UK_1.00.010 firmware, which is the latest version of the firmware I can find. When I set up WPA, it uses  encryption technique TPIK.

The other generic information is 

```
$ iwconfig wlan0 up
04:00.0 Network controller: Intel Corporation WiFi Link 5100
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:074f Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bb4:0c8b High Tech Computer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63fa Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:df:ef:c3  
          inet addr:192.168.2.110  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fedf:efc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:273007 (273.0 KB)  TX bytes:58127 (58.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:27:c5:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
iwlagn                202721  0 
iwlcore               146875  1 iwlagn
mac80211              266657  2 iwlagn,iwlcore
cfg80211              170293  3 iwlagn,iwlcore,mac80211
[   10.895198] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.895201] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.895306] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.895335] iwlagn 0000:04:00.0: setting latency timer to 64
[   10.895408] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.980025] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.980646] iwlagn 0000:04:00.0: irq 46 for MSI/MSI-X
[   11.114455] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
$ lshw -C network
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:27:c5:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-23-generic firmware=8.24.2.12 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:df:ef:c3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb v2.17 ip=192.168.2.110 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:fc500000-fc50ffff
$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:5D:21:CA
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"OFEE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000019960f012
                    Extra: Last beacon: 3170ms ago
                    IE: Unknown: 00044F464545
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:25:86:C2:9E:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"nyaminyami"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000021d0a90792
                    Extra: Last beacon: 3170ms ago
                    IE: Unknown: 000A6E79616D696E79616D69
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706504820010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002586C29E9A022586C29E9A64002C010808

$ lsb_release -d
Description:	Ubuntu 10.10
$ uname -mr
2.6.35-23-generic x86_64

```
My wpa_supplicant.conf file is (I've also tried with the commented lines uncommented).

```

ctrl_interface=/var/run/wpa_supplicant
update_config=1

network={
	ssid="OFEE"
	psk=**big hex string**
#    pairwise=TKIP
#    group=TKIP 
}

```

I've been using this script to try and get wireless enabled - the script worked with the wpa_supplicant line commented out when I had encryption disabled on the router

```

service networking stop
ifconfig wlan0 down
dhclient -r wlan0
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -ddd -t
ifconfig wlan0 192.168.2.110 netmask 255.255.255.0 up
route add default gw 192.168.2.1
ifconfig wlan0 up
iwconfig wlan0 mode Managed
dhclient wlan0

```

This resulted in the following log

```

1291419980.989024: Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
1291419980.989061: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
1291419980.989066: Reading configuration file '/etc/wpa_supplicant.conf'
1291419980.998955: ctrl_interface='/var/run/wpa_supplicant'
1291419980.998962: update_config=1
1291419980.998964: Line: 4 - start of a new network block
1291419980.998974: ssid - hexdump_ascii(len=4):
     4f 46 45 45                                       OFEE            
1291419980.998986: PSK - hexdump(len=32): [REMOVED]
1291419980.998992: pairwise: 0x8
1291419980.998995: group: 0x8
1291419980.999019: Priority group 0
1291419980.999022:    id=0 ssid='OFEE'
1291419980.999025: Initializing interface (2) 'wlan0'
1291419980.999072: WEXT: cfg80211-based driver detected
1291419980.999125: SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
1291419980.999128:   capabilities: key_mgmt 0xf enc 0xf flags 0x0
1291419981.000337: WEXT: Operstate: linkmode=1, operstate=5
1291419981.024348: Own MAC address: 00:21:5d:27:c5:b4
1291419981.024366: wpa_driver_wext_set_wpa
1291419981.024394: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
1291419981.024414: wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
1291419981.024422: wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
1291419981.024429: wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
1291419981.024436: wpa_driver_wext_set_countermeasures
1291419981.024442: wpa_driver_wext_set_drop_unencrypted
1291419981.024447: RSN: flushing PMKID list in the driver
1291419981.024474: Setting scan request: 0 sec 100000 usec
1291419981.024525: WPS: UUID based on MAC address - hexdump(len=16): 84 cd 1a a0 a7 7c 58 f9 85 d7 84 f1 c7 c9 3d 47
1291419981.024546: WPS: Build Beacon and Probe Response IEs
1291419981.024557: WPS:  * Version
1291419981.024563: WPS:  * Wi-Fi Protected Setup State (0)
1291419981.024570: WPS:  * Version
1291419981.024573: WPS:  * Wi-Fi Protected Setup State (0)
1291419981.024576: WPS:  * Response Type (2)
1291419981.024580: WPS:  * UUID-E
1291419981.024586: WPS:  * Manufacturer
1291419981.024589: WPS:  * Model Name
1291419981.024592: WPS:  * Model Number
1291419981.024594: WPS:  * Serial Number
1291419981.024597: WPS:  * Primary Device Type
1291419981.024600: WPS:  * Device Name
1291419981.024610: WPS:  * Config Methods (0)
1291419981.024614: WPS:  * RF Bands (3)
1291419981.026732: EAPOL: SUPP_PAE entering state DISCONNECTED
1291419981.026743: EAPOL: KEY_RX entering state NO_KEY_RECEIVE
1291419981.026746: EAPOL: SUPP_BE entering state INITIALIZE
1291419981.026751: EAP: EAP entering state DISABLED
1291419981.026865: Added interface wlan0
1291419981.026928: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1291419981.026936: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419981.026950: Wireless event: cmd=0x8b06 len=12
1291419981.026958: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1291419981.026963: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419981.026966: Wireless event: cmd=0x8b1a len=16
1291419981.124847: State: DISCONNECTED -> SCANNING
1291419981.124879: Starting AP scan (broadcast SSID)
1291419981.124882: Trying to get current scan results first without requesting a new scan to speed up initial association
1291419981.124933: Received 0 bytes of scan results (0 BSSes)
1291419981.124959: Cached scan results are empty - not posting
1291419981.124964: Selecting BSS from priority group 0
1291419981.124967: Try to find WPA-enabled AP
1291419981.124971: Try to find non-WPA AP
1291419981.124974: No suitable AP found.
1291419981.124979: Setting scan request: 0 sec 0 usec
1291419981.124995: Starting AP scan (broadcast SSID)
1291419981.125340: Scan requested (ret=0) - scan timeout 5 seconds
1291419982.027922: EAPOL: disable timer tick
1291419984.266632: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1291419984.266653: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.266661: Wireless event: cmd=0x8b19 len=16
1291419984.266826: Received 383 bytes of scan results (1 BSSes)
1291419984.266836: New scan results available
1291419984.266858: Selecting BSS from priority group 0
1291419984.266862: Try to find WPA-enabled AP
1291419984.266866: 0: 00:11:50:5d:21:ca ssid='OFEE' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
1291419984.266884:    selected based on WPA IE
1291419984.266887:    selected WPA AP 00:11:50:5d:21:ca ssid='OFEE'
1291419984.266927: Trying to associate with 00:11:50:5d:21:ca (SSID='OFEE' freq=2432 MHz)
1291419984.266937: Cancelling scan request
1291419984.266941: WPA: clearing own WPA/RSN IE
1291419984.266964: Automatic auth_alg selection: 0x1
1291419984.266980: WPA: using IEEE 802.11i/D3.0
1291419984.266994: WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
1291419984.267004: WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1291419984.267021: WPA: clearing AP RSN IE
1291419984.267025: WPA: using GTK TKIP
1291419984.267029: WPA: using PTK TKIP
1291419984.267032: WPA: using KEY_MGMT WPA-PSK
1291419984.267037: WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1291419984.267052: No keys have been configured - skip key clearing
1291419984.267056: wpa_driver_wext_set_drop_unencrypted
1291419984.267062: State: SCANNING -> ASSOCIATING
1291419984.267067: wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
1291419984.267072: WEXT: Operstate: linkmode=-1, operstate=5
1291419984.267093: wpa_driver_wext_associate
1291419984.267117: wpa_driver_wext_set_psk
1291419984.268827: Setting authentication timeout: 10 sec 0 usec
1291419984.268838: EAPOL: External notification - EAP success=0
1291419984.268845: EAPOL: External notification - EAP fail=0
1291419984.268849: EAPOL: External notification - portControl=Auto
1291419984.268923: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1291419984.268931: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.268936: Wireless event: cmd=0x8b06 len=12
1291419984.268943: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1291419984.268947: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.268952: Wireless event: cmd=0x8b1a len=16
1291419984.268957: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1291419984.268962: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.268966: Wireless event: cmd=0x8b04 len=16
1291419984.268971: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1291419984.268976: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.268980: Wireless event: cmd=0x8b1a len=20
1291419984.278254: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1291419984.278268: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.278277: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1291419984.278282: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.278286: Wireless event: cmd=0x8c08 len=40
1291419984.278291: AssocResp IE wireless event - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 01 01 01
1291419984.278311: RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
1291419984.278316: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419984.278320: Wireless event: cmd=0x8b15 len=24
1291419984.278323: Wireless event: new AP: 00:11:50:5d:21:ca
1291419984.278328: Association info event
1291419984.278331: resp_ies - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 01 01 01
1291419984.278348: State: ASSOCIATING -> ASSOCIATED
1291419984.278353: wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
1291419984.278357: WEXT: Operstate: linkmode=-1, operstate=5
1291419984.278384: Associated to a new BSS: BSSID=00:11:50:5d:21:ca
1291419984.278390: No keys have been configured - skip key clearing
1291419984.278395: Associated with 00:11:50:5d:21:ca
1291419984.278399: WPA: Association event - clear replay counter
1291419984.278402: WPA: Clear old PTK
1291419984.278405: EAPOL: External notification - portEnabled=0
1291419984.278488: EAPOL: External notification - portValid=0
1291419984.278492: EAPOL: External notification - EAP success=0
1291419984.278495: EAPOL: External notification - portEnabled=1
1291419984.278500: EAPOL: SUPP_PAE entering state CONNECTING
1291419984.278503: EAPOL: enable timer tick
1291419984.278509: EAPOL: SUPP_BE entering state IDLE
1291419984.278515: Setting authentication timeout: 10 sec 0 usec
1291419984.278522: Cancelling scan request
1291419984.280665: RX EAPOL from 00:11:50:5d:21:ca
1291419984.280673: RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1291419984.280724: Setting authentication timeout: 10 sec 0 usec
1291419984.280740: IEEE 802.1X RX: version=1 type=3 length=95
1291419984.280744:   EAPOL-Key type=254
1291419984.280748:   key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
1291419984.280754:   key_length=32 key_data_length=0
1291419984.280758:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419984.280765:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e0
1291419984.280782:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1291419984.280792:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419984.280799:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419984.280807:   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1291419984.280819: WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1291419984.280877: State: ASSOCIATED -> 4WAY_HANDSHAKE
1291419984.280882: WPA: RX message 1 of 4-Way Handshake from 00:11:50:5d:21:ca (ver=1)
1291419984.282831: WPA: Renewed SNonce - hexdump(len=32): db 20 9c 11 e2 19 b7 81 4f 17 88 07 6d ac 01 f6 0b 70 a3 2c fb 98 31 91 4d a5 d9 a6 fa 7e 7c 1f
1291419984.282881: WPA: PTK derivation - A1=00:21:5d:27:c5:b4 A2=00:11:50:5d:21:ca
1291419984.282889: WPA: PMK - hexdump(len=32): [REMOVED]
1291419984.282892: WPA: PTK - hexdump(len=64): [REMOVED]
1291419984.282900: WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1291419984.282921: WPA: Sending EAPOL-Key 2/4
1291419984.282950: WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 db 20 9c 11 e2 19 b7 81 4f 17 88 07 6d ac 01 f6 0b 70 a3 2c fb 98 31 91 4d a5 d9 a6 fa 7e 7c 1f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7a c2 4a c9 e3 a8 a6 75 28 4b d0 1f 5b 97 4d 28 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1291419984.285853: RX EAPOL from 00:11:50:5d:21:ca
1291419984.285861: RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 01 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7e 95 be c6 e2 81 44 25 c8 f7 0b af 04 1c 44 ce 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1291419984.285919: IEEE 802.1X RX: version=1 type=3 length=119
1291419984.285924:   EAPOL-Key type=254
1291419984.285927:   key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
1291419984.285934:   key_length=32 key_data_length=24
1291419984.285938:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
1291419984.285945:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e0
1291419984.286008:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1291419984.286019:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419984.286026:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419984.286033:   key_mic - hexdump(len=16): 7e 95 be c6 e2 81 44 25 c8 f7 0b af 04 1c 44 ce
1291419984.286045: WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 01 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7e 95 be c6 e2 81 44 25 c8 f7 0b af 04 1c 44 ce 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1291419984.286110: State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
1291419984.286114: WPA: RX message 3 of 4-Way Handshake from 00:11:50:5d:21:ca (ver=1)
1291419984.286121: WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
1291419984.286139: WPA: Sending EAPOL-Key 4/4
1291419984.286145: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 93 5b 4e 60 65 ad c8 e5 ba 58 51 3a 87 0e f6 0f 00 00
1291419984.286210: WPA: Installing PTK to the driver.
1291419984.286215: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291419984.286222: wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
1291419984.286255: State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
1291419984.289000: RX EAPOL from 00:11:50:5d:21:ca
1291419984.289008: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 02 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 df 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e1 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0c ab 60 ff a4 3b ab fc 9c ea 3c 1d 92 c2 48 57 00 20 eb 76 45 86 bd 5f 63 85 53 9a 68 6a 83 e0 43 bd 9d c9 98 35 57 9f 53 02 ca c6 ed be 09 75 dc 64
1291419984.289067: IEEE 802.1X RX: version=1 type=3 length=127
1291419984.289071:   EAPOL-Key type=254
1291419984.289075:   key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
1291419984.289081:   key_length=32 key_data_length=32
1291419984.289085:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
1291419984.289092:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 df
1291419984.289108:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e1
1291419984.289118:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419984.289125:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419984.289132:   key_mic - hexdump(len=16): 0c ab 60 ff a4 3b ab fc 9c ea 3c 1d 92 c2 48 57
1291419984.289143: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 02 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 df 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e1 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0c ab 60 ff a4 3b ab fc 9c ea 3c 1d 92 c2 48 57 00 20 eb 76 45 86 bd 5f 63 85 53 9a 68 6a 83 e0 43 bd 9d c9 98 35 57 9f 53 02 ca c6 ed be 09 75 dc 64
1291419984.289208: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291419984.289222: State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
1291419984.289226: WPA: Group Key - hexdump(len=32): [REMOVED]
1291419984.289230: WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
1291419984.289234: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291419984.289240: wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
1291419984.289259: WPA: Sending EAPOL-Key 2/2
1291419984.289266: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f2 44 c8 76 49 5e 88 a7 14 95 4b 03 0b 7d a6 64 00 00
1291419984.289397: WPA: Key negotiation completed with 00:11:50:5d:21:ca [PTK=TKIP GTK=TKIP]
1291419984.289403: Cancelling authentication timeout
1291419984.289407: State: GROUP_HANDSHAKE -> COMPLETED
1291419984.289415: CTRL-EVENT-CONNECTED - Connection to 00:11:50:5d:21:ca completed (auth) [id=0 id_str=]
1291419984.289419: wpa_driver_wext_set_operstate: operstate 0->1 (UP)
1291419984.289424: WEXT: Operstate: linkmode=-1, operstate=6
1291419984.290634: EAPOL: External notification - portValid=1
1291419984.290640: EAPOL: External notification - EAP success=1
1291419984.290644: EAPOL: SUPP_PAE entering state AUTHENTICATING
1291419984.290648: EAPOL: SUPP_BE entering state SUCCESS
1291419984.290651: EAP: EAP entering state DISABLED
1291419984.290655: EAPOL: SUPP_PAE entering state AUTHENTICATED
1291419984.290657: EAPOL: SUPP_BE entering state IDLE
1291419984.290661: EAPOL authentication completed successfully
1291419984.290687: RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
1291419984.290694: RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
1291419985.279586: EAPOL: startWhen --> 0
1291419985.279599: EAPOL: disable timer tick
1291419989.571737: RX EAPOL from 00:11:50:5d:21:ca
1291419989.571756: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e1 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e2 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 89 a8 97 0c 20 92 bc 7a dc e4 db a3 3e 63 c0 17 00 20 cc 2d 7b 76 75 76 65 92 cb b4 f6 ec 26 d9 b5 ed f0 ca 63 66 91 94 78 2f 2f 84 45 dd d3 f2 7b 20
1291419989.571822: IEEE 802.1X RX: version=1 type=3 length=127
1291419989.571827:   EAPOL-Key type=254
1291419989.571831:   key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
1291419989.571837:   key_length=32 key_data_length=32
1291419989.571841:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
1291419989.571848:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e1
1291419989.571864:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e2
1291419989.571874:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419989.571881:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291419989.571888:   key_mic - hexdump(len=16): 89 a8 97 0c 20 92 bc 7a dc e4 db a3 3e 63 c0 17
1291419989.571903: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e1 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e2 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 89 a8 97 0c 20 92 bc 7a dc e4 db a3 3e 63 c0 17 00 20 cc 2d 7b 76 75 76 65 92 cb b4 f6 ec 26 d9 b5 ed f0 ca 63 66 91 94 78 2f 2f 84 45 dd d3 f2 7b 20
1291419989.571974: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291419989.571988: State: COMPLETED -> GROUP_HANDSHAKE
1291419989.571993: WPA: Group Key - hexdump(len=32): [REMOVED]
1291419989.571997: WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
1291419989.572001: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291419989.572008: wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
1291419989.572053: WPA: Sending EAPOL-Key 2/2
1291419989.572062: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8d e0 2f 63 d6 44 ac 6d cc ef 1a af df da d3 9a 00 00
1291419989.572159: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291419989.572165: Cancelling authentication timeout
1291419989.572289: State: GROUP_HANDSHAKE -> COMPLETED
1291420003.791160: RX EAPOL from 00:11:50:5d:21:ca
1291420003.791178: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 04 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e2 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 9a a5 50 ea fd da 6d 1d 30 02 b3 c6 48 57 7e 00 20 37 b9 c7 7a 8c db fd a6 35 ad 05 e4 a2 3f 5f 1b df 08 e2 42 be d2 0a e8 b7 f6 b1 c2 86 83 ae 2d
1291420003.791243: IEEE 802.1X RX: version=1 type=3 length=127
1291420003.791248:   EAPOL-Key type=254
1291420003.791251:   key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
1291420003.791258:   key_length=32 key_data_length=32
1291420003.791262:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 04
1291420003.791269:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e2
1291420003.791285:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e3
1291420003.791295:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420003.791302:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420003.791309:   key_mic - hexdump(len=16): 12 9a a5 50 ea fd da 6d 1d 30 02 b3 c6 48 57 7e
1291420003.791324: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 04 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e2 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 9a a5 50 ea fd da 6d 1d 30 02 b3 c6 48 57 7e 00 20 37 b9 c7 7a 8c db fd a6 35 ad 05 e4 a2 3f 5f 1b df 08 e2 42 be d2 0a e8 b7 f6 b1 c2 86 83 ae 2d
1291420003.791395: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291420003.791409: State: COMPLETED -> GROUP_HANDSHAKE
1291420003.791414: WPA: Group Key - hexdump(len=32): [REMOVED]
1291420003.791418: WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
1291420003.791422: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291420003.791429: wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
1291420003.791467: WPA: Sending EAPOL-Key 2/2
1291420003.791475: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cd 95 86 fe 15 fe e7 dd 3b 20 34 3c 9e ee 57 51 00 00
1291420003.791567: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291420003.791573: Cancelling authentication timeout
1291420003.791578: State: GROUP_HANDSHAKE -> COMPLETED
1291420017.831072: RX EAPOL from 00:11:50:5d:21:ca
1291420017.831090: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 05 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e3 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 63 4f c8 6d d1 ac d6 f9 6b 1c dc 5d ee 28 3b 6d 00 20 cf 9a 71 3e 94 1a ec 08 14 c3 5a 5d df 86 67 b6 92 c3 6c 6f 40 63 b6 a5 07 ce 02 cf 47 51 ba d9
1291420017.831155: IEEE 802.1X RX: version=1 type=3 length=127
1291420017.831161:   EAPOL-Key type=254
1291420017.831164:   key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
1291420017.831171:   key_length=32 key_data_length=32
1291420017.831174:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 05
1291420017.831182:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e3
1291420017.831198:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e4
1291420017.831207:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420017.831215:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420017.831222:   key_mic - hexdump(len=16): 63 4f c8 6d d1 ac d6 f9 6b 1c dc 5d ee 28 3b 6d
1291420017.831355: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 05 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e3 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 63 4f c8 6d d1 ac d6 f9 6b 1c dc 5d ee 28 3b 6d 00 20 cf 9a 71 3e 94 1a ec 08 14 c3 5a 5d df 86 67 b6 92 c3 6c 6f 40 63 b6 a5 07 ce 02 cf 47 51 ba d9
1291420017.831430: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291420017.831445: State: COMPLETED -> GROUP_HANDSHAKE
1291420017.831450: WPA: Group Key - hexdump(len=32): [REMOVED]
1291420017.831454: WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
1291420017.831459: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291420017.831466: wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
1291420017.831518: WPA: Sending EAPOL-Key 2/2
1291420017.831528: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f3 91 a7 95 18 2c f0 ea e7 56 3f 02 c8 2d 30 0a 00 00
1291420017.831638: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291420017.831645: Cancelling authentication timeout
1291420017.831649: State: GROUP_HANDSHAKE -> COMPLETED
1291420031.850945: RX EAPOL from 00:11:50:5d:21:ca
1291420031.850965: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 06 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e4 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5c 55 4e 13 49 ef 32 a5 25 cf 8a 09 d5 80 0f 5d 00 20 98 0b 1a d0 51 dc df 48 fc 62 35 4b a1 c9 85 a8 06 3d 9e 66 6f 57 1d d5 c0 d0 fa 35 d3 ee 04 d2
1291420031.851030: IEEE 802.1X RX: version=1 type=3 length=127
1291420031.851036:   EAPOL-Key type=254
1291420031.851039:   key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
1291420031.851046:   key_length=32 key_data_length=32
1291420031.851049:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 06
1291420031.851057:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e4
1291420031.851073:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e5
1291420031.851083:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420031.851090:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420031.851097:   key_mic - hexdump(len=16): 5c 55 4e 13 49 ef 32 a5 25 cf 8a 09 d5 80 0f 5d
1291420031.851111: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 06 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e4 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5c 55 4e 13 49 ef 32 a5 25 cf 8a 09 d5 80 0f 5d 00 20 98 0b 1a d0 51 dc df 48 fc 62 35 4b a1 c9 85 a8 06 3d 9e 66 6f 57 1d d5 c0 d0 fa 35 d3 ee 04 d2
1291420031.851183: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291420031.851197: State: COMPLETED -> GROUP_HANDSHAKE
1291420031.851202: WPA: Group Key - hexdump(len=32): [REMOVED]
1291420031.851206: WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
1291420031.851210: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291420031.851217: wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
1291420031.851262: WPA: Sending EAPOL-Key 2/2
1291420031.851271: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 06 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 84 f1 73 80 e6 b7 2a 9a 06 34 a1 81 66 66 93 f6 00 00
1291420031.851488: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291420031.851495: Cancelling authentication timeout
1291420031.851499: State: GROUP_HANDSHAKE -> COMPLETED
1291420045.890756: RX EAPOL from 00:11:50:5d:21:ca
1291420045.890774: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 07 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e5 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e6 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a6 c2 e2 49 11 e0 5d 5d 6c 7d 53 30 3e 17 66 ff 00 20 e6 ea 96 6c 48 d4 f0 2a 23 09 27 da bc 21 14 29 b2 85 98 57 d6 f5 a0 22 30 d7 8e 20 13 da d7 29
1291420045.890840: IEEE 802.1X RX: version=1 type=3 length=127
1291420045.890845:   EAPOL-Key type=254
1291420045.890848:   key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
1291420045.890855:   key_length=32 key_data_length=32
1291420045.890859:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 07
1291420045.890866:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e5
1291420045.890883:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e6
1291420045.890892:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420045.890899:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420045.890906:   key_mic - hexdump(len=16): a6 c2 e2 49 11 e0 5d 5d 6c 7d 53 30 3e 17 66 ff
1291420045.890920: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 07 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e5 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e6 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a6 c2 e2 49 11 e0 5d 5d 6c 7d 53 30 3e 17 66 ff 00 20 e6 ea 96 6c 48 d4 f0 2a 23 09 27 da bc 21 14 29 b2 85 98 57 d6 f5 a0 22 30 d7 8e 20 13 da d7 29
1291420045.890991: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291420045.891006: State: COMPLETED -> GROUP_HANDSHAKE
1291420045.891011: WPA: Group Key - hexdump(len=32): [REMOVED]
1291420045.891015: WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
1291420045.891019: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291420045.891025: wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
1291420045.891073: WPA: Sending EAPOL-Key 2/2
1291420045.891082: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 4e 2e 8c 3b 0a 4c 5a da d6 96 7c 9d d1 04 3e d6 00 00
1291420045.891180: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291420045.891186: Cancelling authentication timeout
1291420045.891190: State: GROUP_HANDSHAKE -> COMPLETED
1291420059.910716: RX EAPOL from 00:11:50:5d:21:ca
1291420059.910734: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 08 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e6 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e7 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 68 f2 d7 ad 2b 6b 5b 27 89 c8 fc 22 68 da 3a 9a 00 20 8c 55 ae a4 70 f3 7e 1f 9b 30 e1 9b 8b 32 57 fe ce d3 c9 7a ae e7 5d ec d0 cb 6d 98 5a 53 72 33
1291420059.910800: IEEE 802.1X RX: version=1 type=3 length=127
1291420059.910805:   EAPOL-Key type=254
1291420059.910808:   key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
1291420059.910815:   key_length=32 key_data_length=32
1291420059.910819:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 08
1291420059.910826:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e6
1291420059.910842:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e7
1291420059.910852:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420059.910986:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420059.910994:   key_mic - hexdump(len=16): 68 f2 d7 ad 2b 6b 5b 27 89 c8 fc 22 68 da 3a 9a
1291420059.911009: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 08 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e6 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e7 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 68 f2 d7 ad 2b 6b 5b 27 89 c8 fc 22 68 da 3a 9a 00 20 8c 55 ae a4 70 f3 7e 1f 9b 30 e1 9b 8b 32 57 fe ce d3 c9 7a ae e7 5d ec d0 cb 6d 98 5a 53 72 33
1291420059.911081: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291420059.911096: State: COMPLETED -> GROUP_HANDSHAKE
1291420059.911104: WPA: Group Key - hexdump(len=32): [REMOVED]
1291420059.911108: WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
1291420059.911112: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291420059.911119: wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
1291420059.911170: WPA: Sending EAPOL-Key 2/2
1291420059.911181: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cc e5 8f 11 e8 79 b8 c9 8d 81 11 0e ff 8c 5d c3 00 00
1291420059.911292: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291420059.911299: Cancelling authentication timeout
1291420059.911304: State: GROUP_HANDSHAKE -> COMPLETED
1291420073.911676: RX EAPOL from 00:11:50:5d:21:ca
1291420073.911692: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 09 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e7 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c9 5c 2d 40 47 ec cc b2 fd fc 49 09 2d d5 77 5a 00 20 ce c8 ff ec 6d 5c 67 d2 71 bf c0 e1 24 96 04 d2 91 35 53 7d ec 2b c0 36 7f ef fe fe b9 25 13 8e
1291420073.911757: IEEE 802.1X RX: version=1 type=3 length=127
1291420073.911764:   EAPOL-Key type=254
1291420073.911767:   key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
1291420073.911774:   key_length=32 key_data_length=32
1291420073.911777:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 09
1291420073.911785:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e7
1291420073.911801:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e8
1291420073.911811:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420073.911818:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420073.911825:   key_mic - hexdump(len=16): c9 5c 2d 40 47 ec cc b2 fd fc 49 09 2d d5 77 5a
1291420073.911839: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 09 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e7 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c9 5c 2d 40 47 ec cc b2 fd fc 49 09 2d d5 77 5a 00 20 ce c8 ff ec 6d 5c 67 d2 71 bf c0 e1 24 96 04 d2 91 35 53 7d ec 2b c0 36 7f ef fe fe b9 25 13 8e
1291420073.911910: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291420073.911924: State: COMPLETED -> GROUP_HANDSHAKE
1291420073.911931: WPA: Group Key - hexdump(len=32): [REMOVED]
1291420073.911935: WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
1291420073.911939: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291420073.911946: wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
1291420073.911985: WPA: Sending EAPOL-Key 2/2
1291420073.911993: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 09 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 63 bf ff 58 90 78 6d 1f 1f 89 a6 1a 2d 8a 53 35 00 00
1291420073.912197: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291420073.912203: Cancelling authentication timeout
1291420073.912207: State: GROUP_HANDSHAKE -> COMPLETED
1291420088.000094: RX EAPOL from 00:11:50:5d:21:ca
1291420088.000112: RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 0a 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e8 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e9 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6b 57 0d 45 78 89 04 96 ce 11 53 0e e4 31 14 03 00 20 66 14 6a 08 c7 3b 9e be b7 d6 8e 60 b3 76 c0 d4 76 f6 1c a8 72 ad 01 57 6c 72 64 e1 b6 74 23 68
1291420088.000178: IEEE 802.1X RX: version=1 type=3 length=127
1291420088.000183:   EAPOL-Key type=254
1291420088.000186:   key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
1291420088.000193:   key_length=32 key_data_length=32
1291420088.000197:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 0a
1291420088.000204:   key_nonce - hexdump(len=32): 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e8
1291420088.000220:   key_iv - hexdump(len=16): 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e9
1291420088.000230:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420088.000237:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1291420088.000244:   key_mic - hexdump(len=16): 6b 57 0d 45 78 89 04 96 ce 11 53 0e e4 31 14 03
1291420088.000258: WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 0a 9f 74 f6 e3 3c 91 c7 73 49 19 b0 86 92 4e 8d 07 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e8 9f 22 55 b2 1e 1e bb ab fe 7f fb 38 61 b3 a4 e9 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6b 57 0d 45 78 89 04 96 ce 11 53 0e e4 31 14 03 00 20 66 14 6a 08 c7 3b 9e be b7 d6 8e 60 b3 76 c0 d4 76 f6 1c a8 72 ad 01 57 6c 72 64 e1 b6 74 23 68
1291420088.000331: WPA: RX message 1 of Group Key Handshake from 00:11:50:5d:21:ca (ver=1)
1291420088.000345: State: COMPLETED -> GROUP_HANDSHAKE
1291420088.000350: WPA: Group Key - hexdump(len=32): [REMOVED]
1291420088.000354: WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
1291420088.000358: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
1291420088.000365: wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
1291420088.000412: WPA: Sending EAPOL-Key 2/2
1291420088.000421: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 0a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 42 68 20 fa d1 9a b8 6d 92 e0 8c 1e 6c 63 21 7d 00 00
1291420088.000520: WPA: Group rekeying completed with 00:11:50:5d:21:ca [GTK=TKIP]
1291420088.000526: Cancelling authentication timeout
1291420088.000530: State: GROUP_HANDSHAKE -> COMPLETED
1291420088.064196: CTRL-EVENT-TERMINATING - signal 2 received
1291420088.064210: Removing interface wlan0
1291420088.064214: wpa_driver_wext_deauthenticate
1291420088.104809: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
1291420088.128012: wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
1291420088.128043: wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
1291420088.128051: wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
1291420088.128059: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
1291420088.128067: State: COMPLETED -> DISCONNECTED
1291420088.128074: wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
1291420088.128079: WEXT: Operstate: linkmode=-1, operstate=5
1291420088.128100: EAPOL: External notification - portEnabled=0
1291420088.128105: EAPOL: SUPP_PAE entering state DISCONNECTED
1291420088.128108: EAPOL: SUPP_BE entering state INITIALIZE
1291420088.128215: EAPOL: External notification - portValid=0
1291420088.128220: EAPOL: External notification - EAP success=0
1291420088.128225: wpa_driver_wext_set_wpa
1291420088.128233: wpa_driver_wext_set_drop_unencrypted
1291420088.128238: wpa_driver_wext_set_countermeasures
1291420088.128245: No keys have been configured - skip key clearing
1291420088.147097: Cancelling scan request
1291420088.147108: Cancelling authentication timeout
1291420088.147153: WEXT: Operstate: linkmode=0, operstate=6

```

I'm stumped and have lost a lot of time trying to get things going. Any help would be greatly appreciated.

---

### Post by tprice1960 on 2010-11-27
Same connection problems.  Dell Precision M6400, Ubuntu 10.10, will not connect to Belkin router or Zyxel Zywall router using wpa-psk.   Will connect to an old Dlink DWL2100 access point using wpa-psk.

---

