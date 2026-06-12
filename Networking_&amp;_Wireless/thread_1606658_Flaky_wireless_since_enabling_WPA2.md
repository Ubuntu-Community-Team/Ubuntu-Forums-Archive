---
title: "Flaky wireless since enabling WPA2"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by clconway on 2010-10-26
I've got a BCM 4312 card on a Dell laptop running 10.04 and an Apple Airport network. Since I configured the Airport to use "WPA2 Personal" Authentication, my connection is flaky: it drops for no apparent reason and sometimes I can't connect at all. When authentication is turned off, the connection is rock solid.

Here's an example from the syslog of a failed attempt to connect:

```
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) starting connection 'Auto Rittenhouse'
Oct 26 19:31:24 firefly NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 26 19:31:24 firefly NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto Rittenhouse' has security, but secrets are required.
Oct 26 19:31:24 firefly NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 26 19:31:24 firefly NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 26 19:31:24 firefly NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto Rittenhouse' has security, and secrets exist.  No new secrets needed.
Oct 26 19:31:24 firefly NetworkManager: <info>  Config: added 'ssid' value 'Rittenhouse'
Oct 26 19:31:24 firefly NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 26 19:31:24 firefly NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct 26 19:31:24 firefly NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct 26 19:31:24 firefly NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 26 19:31:24 firefly NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 26 19:31:24 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 26 19:31:24 firefly NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 26 19:31:24 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct 26 19:31:24 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:31:29 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 26 19:31:29 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct 26 19:31:29 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 26 19:31:29 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct 26 19:31:29 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct 26 19:31:29 firefly wpa_supplicant[1074]: WPA: Key negotiation completed with 00:17:f2:e4:da:d7 [PTK=CCMP GTK=CCMP]
Oct 26 19:31:29 firefly NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Rittenhouse'.
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct 26 19:31:29 firefly NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Oct 26 19:31:29 firefly wpa_supplicant[1074]: CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (auth) [id=1 id_str=]
Oct 26 19:31:29 firefly NetworkManager: <info>  dhclient started with pid 14514
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Oct 26 19:31:29 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 26 19:31:29 firefly dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct 26 19:31:29 firefly dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct 26 19:31:29 firefly dhclient: All rights reserved.
Oct 26 19:31:29 firefly dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 26 19:31:29 firefly dhclient: 
Oct 26 19:31:29 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 26 19:31:29 firefly NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associated
Oct 26 19:31:29 firefly NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Oct 26 19:31:29 firefly dhclient: Listening on LPF/eth1/70:1a:04:a6:34:e1
Oct 26 19:31:29 firefly dhclient: Sending on   LPF/eth1/70:1a:04:a6:34:e1
Oct 26 19:31:29 firefly dhclient: Sending on   Socket/fallback
Oct 26 19:31:31 firefly dhclient: DHCPREQUEST of 192.168.1.31 on eth1 to 255.255.255.255 port 67
Oct 26 19:31:37 firefly dhclient: DHCPREQUEST of 192.168.1.31 on eth1 to 255.255.255.255 port 67
Oct 26 19:31:39 firefly wpa_supplicant[1074]: Authentication with 00:17:f2:e4:da:d7 timed out.
Oct 26 19:31:39 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct 26 19:31:39 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 26 19:31:39 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:31:39 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct 26 19:31:45 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:31:47 firefly dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct 26 19:31:50 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 26 19:31:50 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 26 19:31:50 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct 26 19:31:51 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 26 19:31:51 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct 26 19:31:51 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 26 19:31:51 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:31:54 firefly wpa_supplicant[1074]: last message repeated 2 times
Oct 26 19:31:54 firefly dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Oct 26 19:31:54 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:31:55 firefly NetworkManager: <info>  eth1: link timed out.
Oct 26 19:31:56 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:32:00 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:32:01 firefly wpa_supplicant[1074]: Authentication with 00:17:f2:e4:da:d7 timed out.
Oct 26 19:32:01 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 26 19:32:01 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct 26 19:32:01 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:32:01 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct 26 19:32:04 firefly dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Oct 26 19:32:07 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:32:12 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 26 19:32:12 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 26 19:32:12 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct 26 19:32:12 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct 26 19:32:12 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 26 19:32:12 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 26 19:32:12 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:32:15 firefly wpa_supplicant[1074]: last message repeated 2 times
Oct 26 19:32:15 firefly NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
Oct 26 19:32:15 firefly NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 14514
Oct 26 19:32:15 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct 26 19:32:15 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct 26 19:32:15 firefly NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)
Oct 26 19:32:15 firefly NetworkManager: <info>  Activation (eth1) failed for access point (Rittenhouse)
Oct 26 19:32:15 firefly NetworkManager: <info>  Marking connection 'Auto Rittenhouse' invalid.
Oct 26 19:32:15 firefly NetworkManager: <info>  Activation (eth1) failed.
Oct 26 19:32:15 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct 26 19:32:15 firefly NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Oct 26 19:32:15 firefly NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Oct 26 19:32:15 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

And here's an example of a successful attempt:

```
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): preparing device.
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
Oct 26 19:35:31 firefly wpa_supplicant[1074]: WPS-AP-AVAILABLE 
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) starting connection 'Auto Rittenhouse'
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto Rittenhouse' has security, but secrets are required.
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto Rittenhouse' has security, and secrets exist.  No new secrets needed.
Oct 26 19:35:31 firefly NetworkManager: <info>  Config: added 'ssid' value 'Rittenhouse'
Oct 26 19:35:31 firefly NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 26 19:35:31 firefly NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct 26 19:35:31 firefly NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct 26 19:35:31 firefly NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 26 19:35:31 firefly NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 26 19:35:31 firefly NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct 26 19:35:31 firefly NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 26 19:35:31 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:35:31 firefly anacron[15002]: Anacron 2.3 started on 2010-10-26
Oct 26 19:35:31 firefly anacron[15002]: Normal exit (0 jobs run)
Oct 26 19:35:32 firefly avahi-daemon[1036]: Registering new address record for fe80::721a:4ff:fea6:34e1 on eth1.*.
Oct 26 19:35:32 firefly kernel: [98832.053066] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input54
Oct 26 19:35:32 firefly kernel: [98832.081460] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input55
Oct 26 19:35:41 firefly kernel: [98840.891472] eth1: no IPv6 routers present
Oct 26 19:35:42 firefly wpa_supplicant[1074]: WPS-AP-AVAILABLE 
Oct 26 19:35:42 firefly wpa_supplicant[1074]: Trying to associate with 00:17:f2:e4:da:d7 (SSID='Rittenhouse' freq=2447 MHz)
Oct 26 19:35:42 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct 26 19:35:42 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 26 19:35:42 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct 26 19:35:42 firefly wpa_supplicant[1074]: Associated with 00:00:00:00:00:00
Oct 26 19:35:42 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 26 19:35:42 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 26 19:35:42 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct 26 19:35:42 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:35:46 firefly NetworkManager: <info>  eth1: link timed out.
Oct 26 19:35:46 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> 4-way handshake
Oct 26 19:35:46 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 26 19:35:46 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 26 19:35:46 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 26 19:35:46 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct 26 19:35:46 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:35:49 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> 4-way handshake
Oct 26 19:35:49 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 26 19:35:49 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 26 19:35:49 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:35:51 firefly wpa_supplicant[1074]: last message repeated 2 times
Oct 26 19:35:51 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 26 19:35:51 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 26 19:35:51 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> associating
Oct 26 19:35:51 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 26 19:35:51 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct 26 19:35:51 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 26 19:35:51 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:36:01 firefly wpa_supplicant[1074]: last message repeated 4 times
Oct 26 19:36:01 firefly NetworkManager: <info>  eth1: link timed out.
Oct 26 19:36:01 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 26 19:36:01 firefly wpa_supplicant[1074]: Authentication with 00:17:f2:e4:da:d7 timed out.
Oct 26 19:36:01 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct 26 19:36:01 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:36:01 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 26 19:36:01 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct 26 19:36:07 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 26 19:36:12 firefly wpa_supplicant[1074]: WPS-AP-AVAILABLE 
Oct 26 19:36:12 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 26 19:36:12 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 26 19:36:12 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct 26 19:36:13 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 26 19:36:13 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Oct 26 19:36:13 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Oct 26 19:36:13 firefly wpa_supplicant[1074]: WPA: Key negotiation completed with 00:17:f2:e4:da:d7 [PTK=CCMP GTK=CCMP]
Oct 26 19:36:13 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct 26 19:36:13 firefly wpa_supplicant[1074]: CTRL-EVENT-CONNECTED - Connection to 00:17:f2:e4:da:d7 completed (auth) [id=0 id_str=]
Oct 26 19:36:13 firefly NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Rittenhouse'.
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct 26 19:36:13 firefly NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Oct 26 19:36:13 firefly NetworkManager: <info>  dhclient started with pid 15032
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Oct 26 19:36:13 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 26 19:36:13 firefly dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct 26 19:36:13 firefly dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct 26 19:36:13 firefly dhclient: All rights reserved.
Oct 26 19:36:13 firefly dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 26 19:36:13 firefly dhclient: 
Oct 26 19:36:13 firefly NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Oct 26 19:36:13 firefly dhclient: Listening on LPF/eth1/70:1a:04:a6:34:e1
Oct 26 19:36:13 firefly dhclient: Sending on   LPF/eth1/70:1a:04:a6:34:e1
Oct 26 19:36:13 firefly dhclient: Sending on   Socket/fallback
Oct 26 19:36:17 firefly dhclient: DHCPREQUEST of 192.168.1.31 on eth1 to 255.255.255.255 port 67
Oct 26 19:36:17 firefly dhclient: DHCPACK of 192.168.1.31 from 192.168.1.1
Oct 26 19:36:17 firefly dhclient: bound to 192.168.1.31 -- renewal in 35462 seconds.
Oct 26 19:36:17 firefly NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
Oct 26 19:36:17 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 26 19:36:17 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Oct 26 19:36:17 firefly NetworkManager: <info>    address 192.168.1.31
Oct 26 19:36:17 firefly NetworkManager: <info>    prefix 24 (255.255.255.0)
Oct 26 19:36:17 firefly NetworkManager: <info>    gateway 192.168.1.1
Oct 26 19:36:17 firefly NetworkManager: <info>    hostname 'firefly'
Oct 26 19:36:17 firefly NetworkManager: <info>    nameserver '192.168.1.1'
Oct 26 19:36:17 firefly NetworkManager: <info>    domain name 'westell.com'
Oct 26 19:36:17 firefly NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct 26 19:36:17 firefly NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 26 19:36:17 firefly NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Oct 26 19:36:17 firefly avahi-daemon[1036]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.31.
Oct 26 19:36:17 firefly avahi-daemon[1036]: New relevant interface eth1.IPv4 for mDNS.
Oct 26 19:36:17 firefly avahi-daemon[1036]: Registering new address record for 192.168.1.31 on eth1.IPv4.
Oct 26 19:36:18 firefly NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Oct 26 19:36:18 firefly NetworkManager: <info>  Policy set 'Auto Rittenhouse' (eth1) as default for routing and DNS.
Oct 26 19:36:18 firefly NetworkManager: <info>  Activation (eth1) successful, device activated.
Oct 26 19:36:18 firefly NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.

```

Note that even the successful attempt takes more than 45 seconds; it's 15 seconds before the card is associated with the network and another 15 before a DHCP request is issued. This seems abnormally slow.

Here's an example of the connection being dropped (the drop happens at 15:50, after having connected at 15:30):

```
Oct 26 15:30:54 firefly NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Oct 26 15:30:56 firefly ntpdate[12205]: adjust time server 91.189.94.4 offset -0.258150 sec
Oct 26 15:39:01 firefly CRON[12385]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct 26 15:43:57 firefly wpa_supplicant[1074]: WPA: Group rekeying completed with 00:17:f2:e4:da:d7 [GTK=CCMP]
Oct 26 15:43:57 firefly NetworkManager: <info>  (eth1): supplicant connection state:  completed -> group handshake
Oct 26 15:43:57 firefly NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct 26 15:50:08 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 26 15:50:08 firefly NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associating
Oct 26 15:50:08 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 26 15:50:08 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake

```

Any tips?

---

### Post by kreggz on 2010-10-27
Are there any firmware updates available for the Access Point?

---

### Post by clconway on 2010-10-27
> **kreggz said:**
> Are there any firmware updates available for the Access Point?

AFAICT no.

---

### Post by clconway on 2010-10-27
Some extra details: the network is a WDS network with two APs, one main (an Airport Extreme) and one remote (an Airport Express). My wife's computer (a Mac) reliably connects quickly with no problem.

---

### Post by clconway on 2010-10-27
Here's another example of a dropped connection. The connection is made at 10:17:42 and drops sometime before 10:19:18, but it's not until 10:19:18 that Network Manager visibly starts the attempt to reconnect (i.e., I had network processes hanging for several seconds before the notification applet changed state).

```
Oct 27 10:17:42 firefly NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Oct 27 10:17:42 firefly NetworkManager: <info>  Policy set 'Auto Rittenhouse' (eth1) as default for routing and DNS.
Oct 27 10:17:42 firefly NetworkManager: <info>  Activation (eth1) successful, device activated.
Oct 27 10:17:42 firefly NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Oct 27 10:17:44 firefly ntpdate[18487]: adjust time server 91.189.94.4 offset -0.003542 sec
Oct 27 10:18:37 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 27 10:18:37 firefly NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associating
Oct 27 10:18:37 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 27 10:18:37 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct 27 10:18:37 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 27 10:18:37 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 27 10:18:37 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 27 10:18:47 firefly wpa_supplicant[1074]: last message repeated 5 times
Oct 27 10:18:47 firefly wpa_supplicant[1074]: Authentication with 00:17:f2:e4:da:d7 timed out.
Oct 27 10:18:47 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 27 10:18:47 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct 27 10:18:47 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 27 10:18:47 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct 27 10:18:53 firefly NetworkManager: <debug> [1288189133.006193] periodic_update(): Roamed from BSSID 00:17:F2:E4:DA:D7 (Rittenhouse) to (none) ((none))
Oct 27 10:18:53 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 27 10:18:58 firefly wpa_supplicant[1074]: Trying to associate with 00:1f:f3:bf:94:10 (SSID='Rittenhouse' freq=2447 MHz)
Oct 27 10:18:58 firefly wpa_supplicant[1074]: Association request to the driver failed
Oct 27 10:18:58 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct 27 10:18:58 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct 27 10:18:58 firefly wpa_supplicant[1074]: Associated with 00:17:f2:e4:da:d7
Oct 27 10:18:58 firefly NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct 27 10:18:58 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 27 10:18:59 firefly NetworkManager: <debug> [1288189139.001261] periodic_update(): Roamed from BSSID (none) ((none)) to 00:17:F2:E4:DA:D7 (Rittenhouse)
Oct 27 10:18:59 firefly wpa_supplicant[1074]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct 27 10:19:08 firefly wpa_supplicant[1074]: last message repeated 4 times
Oct 27 10:19:08 firefly wpa_supplicant[1074]: Authentication with 00:17:f2:e4:da:d7 timed out.
Oct 27 10:19:08 firefly wpa_supplicant[1074]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 27 10:19:08 firefly NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct 27 10:19:08 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 27 10:19:08 firefly NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct 27 10:19:11 firefly NetworkManager: <debug> [1288189151.002689] periodic_update(): Roamed from BSSID 00:17:F2:E4:DA:D7 (Rittenhouse) to (none) ((none))
Oct 27 10:19:14 firefly NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct 27 10:19:18 firefly NetworkManager: <info>  (eth1): device state change: 8 -> 3 (reason 11)
Oct 27 10:19:18 firefly NetworkManager: <info>  (eth1): deactivating device (reason: 11).
Oct 27 10:19:18 firefly NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 18430
Oct 27 10:19:18 firefly NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Oct 27 10:19:18 firefly avahi-daemon[1036]: Withdrawing address record for 192.168.1.31 on eth1.
Oct 27 10:19:18 firefly avahi-daemon[1036]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.31.
Oct 27 10:19:18 firefly avahi-daemon[1036]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 27 10:19:18 firefly NetworkManager: <info>  Activation (eth1) starting connection 'Auto Rittenhouse'
```

---

### Post by clconway on 2010-11-11
I solved this problem completely by switching from Network Manager to wicd. The network connects nearly instantly and never drops.

```
sudo apt-get remove --purge network-manager
sudo apt-get install wicd-gtk
```

---

