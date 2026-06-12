---
title: "seggfault in dhcp client"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by fbollens on 2010-08-01
Hello, after installing en testing DVD95 and trying to read an videoiso dvd, my network connection disappears. I see this in my syslog file:

 1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto wirelessdi-524fb'
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto wirelessdi-524fb' has security, but secrets are required.
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto wirelessdi-524fb' has security, and secrets exist.  No new secrets needed.
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Config: added 'ssid' value 'wirelessdi-524fb'
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Aug  1 10:46:05 fb-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  1 10:46:05 fb-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug  1 10:46:05 fb-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  1 10:46:07 fb-desktop wpa_supplicant[752]: Trying to associate with 00:1c:f0:87:e4:90 (SSID='wirelessdi-524fb' freq=2462 MHz)
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  1 10:46:07 fb-desktop kernel: [  312.969803] wlan0: deauthenticating from 00:1c:f0:87:e4:90 by local choice (reason=3)
Aug  1 10:46:07 fb-desktop kernel: [  313.168033] wlan0: direct probe to AP 00:1c:f0:87:e4:90 (try 1)
Aug  1 10:46:07 fb-desktop kernel: [  313.169812] wlan0: direct probe responded
Aug  1 10:46:07 fb-desktop kernel: [  313.169815] wlan0: authenticate with AP 00:1c:f0:87:e4:90 (try 1)
Aug  1 10:46:07 fb-desktop kernel: [  313.173565] wlan0: authenticated
Aug  1 10:46:07 fb-desktop kernel: [  313.173588] wlan0: associate with AP 00:1c:f0:87:e4:90 (try 1)
Aug  1 10:46:07 fb-desktop kernel: [  313.175609] wlan0: RX AssocResp from 00:1c:f0:87:e4:90 (capab=0x431 status=0 aid=1)
Aug  1 10:46:07 fb-desktop kernel: [  313.175612] wlan0: associated
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  1 10:46:07 fb-desktop wpa_supplicant[752]: Associated with 00:1c:f0:87:e4:90
Aug  1 10:46:07 fb-desktop wpa_supplicant[752]: CTRL-EVENT-CONNECTED - Connection to 00:1c:f0:87:e4:90 completed (reauth) [id=0 id_str=]
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wirelessdi-524fb'.
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  dhclient started with pid 1565
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug  1 10:46:07 fb-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug  1 10:46:07 fb-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug  1 10:46:07 fb-desktop dhclient: All rights reserved.
Aug  1 10:46:07 fb-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug  1 10:46:07 fb-desktop dhclient: 
Aug  1 10:46:07 fb-desktop kernel: [  313.187888] dhclient[1565]: segfault at 258096 ip 00230c70 sp bfa1a70c error 7 in dhclient3[1fe000+63000]
Aug  1 10:46:07 fb-desktop NetworkManager: <WARN>  dhcp_watch_cb(): dhcp client died abnormally
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 17)
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) failed for access point (wirelessdi-524fb)
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Marking connection 'Auto wirelessdi-524fb' invalid.
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  Activation (wlan0) failed.
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug  1 10:46:07 fb-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug  1 10:46:07 fb-desktop kernel: [  313.195025] wlan0: deauthenticating from 00:1c:f0:87:e4:90 by local choice (reason=3)
Aug  1 10:46:07 fb-desktop wpa_supplicant[752]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  1 10:46:10 fb-desktop anacron[811]: Job `cron.daily' started
Aug  1 10:46:10 fb-desktop anacron[1571]: Updated timestamp for job `cron.daily' to 2010-08-01
Aug  1 10:47:39 fb-desktop AptDaemon: INFO: Quiting due to inactivity
Aug  1 10:47:39 fb-desktop AptDaemon: INFO: Shutdown was requested

Before everything worked fine.
Fons.

---

