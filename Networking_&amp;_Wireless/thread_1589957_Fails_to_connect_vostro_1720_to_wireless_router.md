---
title: "Fails to connect vostro 1720 to wireless router"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by tirithen on 2010-10-07
Hello, I'm trying to find out why the wireless access point at work most of the time won't let me connect to the network. I'm using Ubuntu 10.04 on a DELL vostro 1720. The router model is D-LINK DIR-655.

lspci gives me: Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01), and I'm using Broardcom STA drivers.

If I try like 10-20 times to connect I will often finally get connected and once connected everything works fine for the rest of the day. The only router I'm having this problem with is this one.

In the log below, the last lines is a connectionattempt that succeeded and all the lines above those are several attempts that failed. It seemes like there is some kind of timeout issue but I'm not sure what and how to fix it.

The syslog for the connection attempts are (I have marked out MAC adesses and public ips with *):
```

Oct  7 11:19:04 computer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Oct  7 11:19:05 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:19:05 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:19:05 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:19:05 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:19:05 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:19:11 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:19:16 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:19:16 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:19:16 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:19:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:19:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:19:16 computer wpa_supplicant[866]: WPA: Key negotiation completed with **:**:**:**:**:** [PTK=CCMP GTK=TKIP]
Oct  7 11:19:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct  7 11:19:16 computer wpa_supplicant[866]: CTRL-EVENT-CONNECTED - Connection to **:**:**:**:**:** completed (reauth) [id=2 id_str=]
Oct  7 11:19:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct  7 11:19:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associated
Oct  7 11:19:16 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:19:22 computer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Oct  7 11:19:26 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:19:26 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:19:26 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:19:26 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:19:26 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:19:32 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:19:37 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:19:37 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:19:37 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:19:37 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:19:38 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:19:38 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:19:38 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct  7 11:19:38 computer wpa_supplicant[866]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct  7 11:19:40 computer NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
Oct  7 11:19:40 computer NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 6828
Oct  7 11:19:40 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct  7 11:19:40 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct  7 11:19:40 computer NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)
Oct  7 11:19:40 computer NetworkManager: <info>  Activation (eth1) failed for access point (access_point)
Oct  7 11:19:40 computer NetworkManager: <info>  Marking connection 'access_point' invalid.
Oct  7 11:19:40 computer NetworkManager: <info>  Activation (eth1) failed.
Oct  7 11:19:40 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct  7 11:19:40 computer NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Oct  7 11:19:40 computer NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Oct  7 11:19:40 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:19:48 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) starting connection 'access_point'
Oct  7 11:20:33 computer NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  7 11:20:33 computer NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1/wireless): access point 'access_point' has security, but secrets are required.
Oct  7 11:20:33 computer NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  7 11:20:33 computer NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  7 11:20:33 computer NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1/wireless): connection 'access_point' has security, and secrets exist.  No new secrets needed.
Oct  7 11:20:33 computer NetworkManager: <info>  Config: added 'ssid' value 'access_point'
Oct  7 11:20:33 computer NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct  7 11:20:33 computer NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct  7 11:20:33 computer NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct  7 11:20:33 computer NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  7 11:20:33 computer NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  7 11:20:33 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  7 11:20:33 computer NetworkManager: <info>  Config: set interface ap_scan to 1
Oct  7 11:20:33 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:20:33 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:20:38 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:20:38 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:20:38 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:20:38 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:20:39 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:20:39 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:20:39 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct  7 11:20:39 computer wpa_supplicant[866]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct  7 11:20:49 computer wpa_supplicant[866]: last message repeated 3 times
Oct  7 11:20:49 computer NetworkManager: <info>  eth1: link timed out.
Oct  7 11:20:49 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:20:49 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:20:49 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:20:49 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:20:49 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:20:55 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:21:00 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:21:00 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:21:00 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:21:00 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:21:00 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:21:00 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:21:00 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct  7 11:21:00 computer wpa_supplicant[866]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct  7 11:21:10 computer wpa_supplicant[866]: last message repeated 3 times
Oct  7 11:21:10 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:21:10 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:21:10 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:21:10 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:21:10 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:21:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:21:19 computer NetworkManager: <info>  eth1: link timed out.
Oct  7 11:21:21 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:21:21 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:21:21 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:21:21 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:21:22 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:21:22 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:21:22 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct  7 11:21:22 computer wpa_supplicant[866]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct  7 11:21:32 computer wpa_supplicant[866]: last message repeated 3 times
Oct  7 11:21:32 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:21:32 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:21:32 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:21:32 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:21:32 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:21:34 computer NetworkManager: <info>  Activation (eth1/wireless): association took too long.
Oct  7 11:21:34 computer NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Oct  7 11:21:34 computer NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
Oct  7 11:21:38 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:21:43 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:21:43 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:21:43 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:21:43 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:21:44 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:21:44 computer wpa_supplicant[866]: WPA: Key negotiation completed with **:**:**:**:**:** [PTK=CCMP GTK=TKIP]
Oct  7 11:21:44 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct  7 11:21:44 computer wpa_supplicant[866]: CTRL-EVENT-CONNECTED - Connection to **:**:**:**:**:** completed (reauth) [id=2 id_str=]
Oct  7 11:21:44 computer NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct  7 11:21:44 computer NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associated
Oct  7 11:21:44 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:21:54 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:21:54 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:21:54 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:21:54 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:21:54 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:22:00 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:22:05 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:22:05 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:22:05 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:22:05 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:22:06 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:22:06 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:22:06 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> associated
Oct  7 11:22:06 computer wpa_supplicant[866]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Oct  7 11:22:16 computer wpa_supplicant[866]: last message repeated 3 times
Oct  7 11:22:16 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:22:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:22:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:22:16 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:22:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:22:16 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  7 11:22:16 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  7 11:22:16 computer NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Oct  7 11:22:16 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  7 11:22:16 computer NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  7 11:22:16 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  7 11:22:16 computer NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct  7 11:22:16 computer NetworkManager: <info>  Activation (eth1/wireless): connection 'access_point' has security, and secrets exist.  No new secrets needed.
Oct  7 11:22:16 computer NetworkManager: <info>  Config: added 'ssid' value 'access_point'
Oct  7 11:22:16 computer NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct  7 11:22:16 computer NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct  7 11:22:16 computer NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct  7 11:22:16 computer NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  7 11:22:16 computer NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  7 11:22:16 computer NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  7 11:22:16 computer NetworkManager: <info>  Config: set interface ap_scan to 1
Oct  7 11:22:16 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:22:27 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:22:27 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:22:27 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:22:27 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:22:28 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> 4-way handshake
Oct  7 11:22:28 computer wpa_supplicant[866]: WPA: Key negotiation completed with **:**:**:**:**:** [PTK=CCMP GTK=TKIP]
Oct  7 11:22:28 computer wpa_supplicant[866]: CTRL-EVENT-CONNECTED - Connection to **:**:**:**:**:** completed (reauth) [id=3 id_str=]
Oct  7 11:22:28 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct  7 11:22:28 computer NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'access_point'.
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  7 11:22:28 computer NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Oct  7 11:22:28 computer NetworkManager: <info>  dhclient started with pid 7378
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Oct  7 11:22:28 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Oct  7 11:22:28 computer dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct  7 11:22:28 computer dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct  7 11:22:28 computer dhclient: All rights reserved.
Oct  7 11:22:28 computer dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  7 11:22:28 computer dhclient: 
Oct  7 11:22:28 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:22:28 computer NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associated
Oct  7 11:22:28 computer NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Oct  7 11:22:28 computer dhclient: Listening on LPF/eth1/**:**:**:**:**:**
Oct  7 11:22:28 computer dhclient: Sending on   LPF/eth1/**:**:**:**:**:**
Oct  7 11:22:28 computer dhclient: Sending on   Socket/fallback
Oct  7 11:22:32 computer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct  7 11:22:38 computer wpa_supplicant[866]: Authentication with **:**:**:**:**:** timed out.
Oct  7 11:22:38 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Oct  7 11:22:38 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:22:38 computer wpa_supplicant[866]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  7 11:22:38 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Oct  7 11:22:39 computer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Oct  7 11:22:44 computer NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Oct  7 11:22:49 computer wpa_supplicant[866]: WPS-AP-AVAILABLE 
Oct  7 11:22:49 computer wpa_supplicant[866]: Trying to associate with **:**:**:**:**:** (SSID='access_point' freq=2437 MHz)
Oct  7 11:22:49 computer wpa_supplicant[866]: Association request to the driver failed
Oct  7 11:22:49 computer NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  7 11:22:50 computer wpa_supplicant[866]: Associated with **:**:**:**:**:**
Oct  7 11:22:50 computer NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Oct  7 11:22:50 computer NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Oct  7 11:22:50 computer wpa_supplicant[866]: WPA: Key negotiation completed with **:**:**:**:**:** [PTK=CCMP GTK=TKIP]
Oct  7 11:22:50 computer NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct  7 11:22:50 computer wpa_supplicant[866]: CTRL-EVENT-CONNECTED - Connection to **:**:**:**:**:** completed (reauth) [id=3 id_str=]
Oct  7 11:22:50 computer NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct  7 11:22:59 computer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Oct  7 11:23:00 computer dhclient: DHCPOFFER of 192.168.0.179 from 192.168.0.1
Oct  7 11:23:00 computer dhclient: DHCPREQUEST of 192.168.0.179 on eth1 to 255.255.255.255 port 67
Oct  7 11:23:00 computer dhclient: DHCPACK of 192.168.0.179 from 192.168.0.1
Oct  7 11:23:00 computer dhclient: bound to 192.168.0.179 -- renewal in 32494 seconds.
Oct  7 11:23:00 computer NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
Oct  7 11:23:00 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct  7 11:23:00 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Oct  7 11:23:00 computer NetworkManager: <info>    address 192.168.0.179
Oct  7 11:23:00 computer NetworkManager: <info>    prefix 24 (255.255.255.0)
Oct  7 11:23:00 computer NetworkManager: <info>    gateway 192.168.0.1
Oct  7 11:23:00 computer NetworkManager: <info>    nameserver '192.168.0.1'
Oct  7 11:23:00 computer NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct  7 11:23:00 computer NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Oct  7 11:23:00 computer NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Oct  7 11:23:00 computer avahi-daemon[812]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.179.
Oct  7 11:23:00 computer avahi-daemon[812]: New relevant interface eth1.IPv4 for mDNS.
Oct  7 11:23:00 computer avahi-daemon[812]: Registering new address record for 192.168.0.179 on eth1.IPv4.
Oct  7 11:23:01 computer NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Oct  7 11:23:01 computer NetworkManager: <info>  Policy set 'access_point' (eth1) as default for routing and DNS.
Oct  7 11:23:01 computer NetworkManager: <info>  Activation (eth1) successful, device activated.
Oct  7 11:23:01 computer NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Oct  7 11:23:02 computer avahi-daemon[812]: Got SIGTERM, quitting.
Oct  7 11:23:02 computer avahi-daemon[812]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.179.
Oct  7 11:23:02 computer init: avahi-daemon main process (812) terminated with status 255
Oct  7 11:23:02 computer avahi: Avahi detected that your currently configured local DNS server serves
Oct  7 11:23:02 computer avahi: a domain .local. This is inherently incompatible with Avahi and thus
Oct  7 11:23:02 computer avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Oct  7 11:23:02 computer avahi: contact your administrator and convince him to use a different DNS domain,
Oct  7 11:23:02 computer avahi: since .local should be used exclusively for Zeroconf technology.
Oct  7 11:23:02 computer avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Oct  7 11:23:03 computer ntpdate[7518]: adjust time server ***.***.***.*** offset -0.079339 sec
Oct  7 11:23:03 computer kernel: [ 1771.160962] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

```

---

### Post by tirithen on 2010-10-14
*bump*

---

### Post by adlerhn on 2011-03-21
I think I am having the same problem.

When I have low signal (25% to 30%), sometimes I can connect to the WLAN AP, sometimes I will be asked again and again for the password (which NetworkManager has already stored).

With exactly the same circumstances, from Windows I can connect at the first attemp, with no problems whatsoever, and not even disconnections.

---

### Post by tomtmx on 2011-04-29
Hi
I had a similar problem, connecting a Dell M6500 to a DLink DIR855.
Remembering that it was working for months until i enabled the "Guest" network in the Dlink,
i disabled that option. Now the problem is fixed for me. Don't know whether dir655 has a guest mode or not, but playing around with wireless options may help.

---

### Post by hexaditidom on 2012-01-16
New user here. I have Lucid, a Netgear WNDA3100 USB wireless adapter, a D-link router, and I have run into this same roadblock. Ndiswrapper works great; a list of networks is displayed, and it sees my network and has good connectivity, but it always times out during authentication. The same adapter connects instantly in windows under the same circumstances.

I entered the network's WPA code using Network Manager.
In syslog, this block is repeated several times (starred out address manually):
```

Jan 16 11:28:58 Furato wpa_supplicant[1024]: WPS-AP-AVAILABLE 
Jan 16 11:28:58 Furato wpa_supplicant[1024]: Trying to associate with **:**:**:**:**:** (SSID='My network' freq=2412 MHz)
Jan 16 11:28:58 Furato NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 16 11:28:59 Furato wpa_supplicant[1024]: Associated with **:**:**:**:**:**
Jan 16 11:28:59 Furato NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan 16 11:28:59 Furato NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan 16 11:29:09 Furato NetworkManager: <info>  wlan0: link timed out.
Jan 16 11:29:09 Furato wpa_supplicant[1024]: Authentication with **:**:**:**:**:** timed out.
Jan 16 11:29:09 Furato NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Jan 16 11:29:09 Furato NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 16 11:29:09 Furato wpa_supplicant[1024]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan 16 11:29:09 Furato NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan 16 11:29:14 Furato wpa_supplicant[1024]: WPS-AP-AVAILABLE 
```

I have tried resetting the modem/router, didn't work.
I'd rather not mess with the router's configuration just yet. I want to try everything else first.
Any help is appreciated.

---

