---
title: "DHCP request with WLAN activation fails"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Rschnauzer on 2010-01-10
Hallo,
the activation of my WLAN Adapter is not successful. The DHCP call seems to fail.
The router (AVM FritzBox 7270) has to messages in the log. 
The router will not react on broadcast pings 255.255.255.255 but on direct ping to the private address 192.168.178.1. The log below shows already the correct address 192.168.178.21. Does anybody know why the wlan activation fails?

```
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) starting connection 'Auto MYSSID'
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto MYSSID' has security, but secrets are required.
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto MYSSID' has security, and secrets exist.  No new secrets needed.
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Config: added 'ssid' value 'MYSSID'
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan 10 19:47:04 BYIZB3 NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 10 19:47:04 BYIZB3 NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  Config: set interface ap_scan to 1
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan 10 19:47:04 BYIZB3 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 10 19:47:05 BYIZB3 wpa_supplicant[1207]: Failed to initiate AP scan.
Jan 10 19:47:05 BYIZB3 wpa_supplicant[1207]: CTRL-EVENT-SCAN-RESULTS 
Jan 10 19:47:05 BYIZB3 wpa_supplicant[1207]: WPS-AP-AVAILABLE 
Jan 10 19:47:05 BYIZB3 wpa_supplicant[1207]: Trying to associate with 00:15:0c:ab:cd:ef (SSID='MYSSID' freq=2412 MHz)
Jan 10 19:47:05 BYIZB3 wpa_supplicant[1207]: Association request to the driver failed
Jan 10 19:47:05 BYIZB3 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 10 19:47:05 BYIZB3 kernel: [11646.857143] wlan0: authenticate with AP 00:15:0c:ab:cd:ef
Jan 10 19:47:05 BYIZB3 kernel: [11646.859652] wlan0: authenticated
Jan 10 19:47:05 BYIZB3 kernel: [11646.859654] wlan0: associate with AP 00:15:0c:ab:cd:ef
Jan 10 19:47:05 BYIZB3 kernel: [11646.867901] wlan0: RX AssocResp from 00:15:0c:ab:cd:ef (capab=0x451 status=0 aid=2)
Jan 10 19:47:05 BYIZB3 kernel: [11646.867904] wlan0: associated
Jan 10 19:47:05 BYIZB3 wpa_supplicant[1207]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Jan 10 19:47:05 BYIZB3 wpa_supplicant[1207]: Associated with 00:15:0c:ab:cd:ef
Jan 10 19:47:05 BYIZB3 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan 10 19:47:06 BYIZB3 wpa_supplicant[1207]: WPA: Key negotiation completed with 00:15:0c:ab:cd:ef [PTK=TKIP GTK=TKIP]
Jan 10 19:47:06 BYIZB3 wpa_supplicant[1207]: CTRL-EVENT-CONNECTED - Connection to 00:15:0c:ab:cd:ef completed (reauth) [id=0 id_str=]
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MYSSID'.
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  dhclient started with pid 3998
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 10 19:47:06 BYIZB3 dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan 10 19:47:06 BYIZB3 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 10 19:47:06 BYIZB3 dhclient: All rights reserved.
Jan 10 19:47:06 BYIZB3 dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 10 19:47:06 BYIZB3 dhclient: 
Jan 10 19:47:06 BYIZB3 NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jan 10 19:47:06 BYIZB3 dhclient: Listening on LPF/wlan0/00:15:af:ab:cd:ef
Jan 10 19:47:06 BYIZB3 dhclient: Sending on   LPF/wlan0/00:15:af:ab:cd:ef
Jan 10 19:47:06 BYIZB3 dhclient: Sending on   Socket/fallback
Jan 10 19:47:09 BYIZB3 dhclient: DHCPREQUEST of 192.168.178.21 on wlan0 to 255.255.255.255 port 67
Jan 10 19:47:16 BYIZB3 dhclient: DHCPREQUEST of 192.168.178.21 on wlan0 to 255.255.255.255 port 67
Jan 10 19:47:16 BYIZB3 dhclient: DHCPNAK from 192.168.178.1
Jan 10 19:47:16 BYIZB3 NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> expire
Jan 10 19:47:16 BYIZB3 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jan 10 19:47:16 BYIZB3 NetworkManager: <info>  DHCP: device wlan0 state changed expire -> preinit
Jan 10 19:47:16 BYIZB3 dhclient: DHCPOFFER of 192.168.178.21 from 192.168.178.1
Jan 10 19:47:16 BYIZB3 dhclient: DHCPREQUEST of 192.168.178.21 on wlan0 to 255.255.255.255 port 67
Jan 10 19:47:24 BYIZB3 dhclient: DHCPREQUEST of 192.168.178.21 on wlan0 to 255.255.255.255 port 67
Jan 10 19:47:39 BYIZB3 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan 10 19:47:47 BYIZB3 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3998
Jan 10 19:47:52 BYIZB3 kernel: [11693.175156] wlan0: disassociating by local choice (reason=3)
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  Activation (wlan0) failed for access point (MYSSID)
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  Marking connection 'Auto MYSSID' invalid.
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  Activation (wlan0) failed.
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jan 10 19:47:52 BYIZB3 NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jan 10 19:47:52 BYIZB3 wpa_supplicant[1207]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan 10 19:48:26 BYIZB3 wpa_supplicant[1207]: CTRL-EVENT-SCAN-RESULTS 
```

---

### Post by Rschnauzer on 2010-01-17
I am not able to connect successfull to the LAN via wlan.
After disconnecting eth0 and activating wlan via NM I got the following results.
NM displays successfull connection, but there is no sucessfull network connection available.
Ping to router and repeater is[COLOR=SeaGreen] sucessfull[/COLOR], http connection to router or internet [COLOR=Red]not successfull[/COLOR]. 
Ping from other local LAN PC ist [COLOR=SeaGreen]successfull[/COLOR].
[FONT=Courier New]```
ebel@BYIZB3:~$ route -ve
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface
192.168.178.0   *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         fritz.box       0.0.0.0         UG        0 0          0 wlan0
```[/FONT]PC connects to repeater (20m off) and not to router (1m off).
```
ebel@BYIZB3:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"EBEL-A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:15:0C:39:6F:2A   
          Bit Rate=36 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-186 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

ebel@BYIZB3:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:15:0C:39:6F:2A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-186 dBm  
                    Encryption key:on
                    ESSID:"EBEL-A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000065ae2f033
                    Extra: Last beacon: 1384ms ago
                    IE: Unknown: 00064542454C2D41
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
          Cell 02 - Address: 00:1F:3F:A1:44:8E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=63 dBm  
                    Encryption key:on
                    ESSID:"EBEL-A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007fdc1de183
                    Extra: Last beacon: 860ms ago
                    IE: Unknown: 00064542454C2D41
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
```What may I do to get a stable wlan connection to the nearby router AP and valid routing to the internet?
In wireshark I did not see any traffic leaving the local net.
After a while the wlan connection is lost with authorization problems (som EAPOL retries).

---

### Post by dluciv on 2010-03-19
Ubuntu 9.10 fails to get settings from DHCP on D-Link DI-604 router, but easily gets from D-Link DWL-G700AP access point.

After setting up statically using ifcofig and route everything works fine.

---

