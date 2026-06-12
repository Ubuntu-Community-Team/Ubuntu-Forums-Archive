---
title: "Unable to connect to WPA network"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by AndySaunders on 2009-12-09
Ubuntu 8.10 was able to connect to WPA networks with my hardware.
Windows was able to connect to WPA networks with my hardware.
9.04 and 9.10 have been unable to connect to WPA networks. WEP is perfectly fine.

I am unable to make changes (or request changes) to the specific router I need to connect to, but I am unable to connect to any WPA networks (I changed my home router's security to WPA from WEP in order to recreate the issue, which I was able to do).

Here is the output of my syslog while attempting to connect:

```

Dec  9 12:57:24 andy-laptop NetworkManager: <info>  (wlan0): bringing up device.
Dec  9 12:57:24 andy-laptop kernel: [ 1123.550415] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  9 12:57:24 andy-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Dec  9 12:57:24 andy-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Dec  9 12:57:24 andy-laptop wpa_supplicant[1107]: CTRL-EVENT-SCAN-RESULTS 
Dec  9 12:57:29 andy-laptop wpa_supplicant[1107]: CTRL-EVENT-SCAN-RESULTS 
Dec  9 12:57:33 andy-laptop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Saunders'
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Saunders' has security, but secrets are required.
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec  9 12:57:33 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  9 12:57:34 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Saunders' has security, and secrets exist.  No new secrets needed.
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Config: added 'ssid' value 'Saunders'
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Dec  9 12:57:43 andy-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  9 12:57:43 andy-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Dec  9 12:57:43 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Dec  9 12:57:49 andy-laptop wpa_supplicant[1107]: CTRL-EVENT-SCAN-RESULTS 
Dec  9 12:57:49 andy-laptop kernel: [ 1148.442500] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Dec  9 12:57:49 andy-laptop wpa_supplicant[1107]: Trying to associate with 00:0f:b5:ee:3d:8e (SSID='Saunders' freq=2462 MHz)
Dec  9 12:57:49 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  9 12:57:49 andy-laptop wpa_supplicant[1107]: Association request to the driver failed
Dec  9 12:57:49 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:57:49 andy-laptop kernel: [ 1148.458049] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec  9 12:57:49 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  9 12:57:49 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:57:49 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:50 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:57:50 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:50 andy-laptop avahi-daemon[898]: Registering new address record for fe80::21c:26ff:fe4f:71de on wlan0.*.
Dec  9 12:57:51 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:57:51 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:52 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:57:52 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:54 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:57:54 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:57:54 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:57:54 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:55 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:57:55 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:56 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:57:56 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:57 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:57:57 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:57:59 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:57:59 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:57:59 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:57:59 andy-laptop kernel: [ 1158.788110] wlan0: no IPv6 routers present
Dec  9 12:58:00 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:01 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:01 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:02 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:02 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:03 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:03 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:05 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:05 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:05 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:05 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:06 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:06 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:07 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:07 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:08 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:08 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:10 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:10 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:10 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:11 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:12 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:12 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:13 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:13 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:14 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:14 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:16 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:16 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:16 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:16 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:17 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:17 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:18 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:18 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:19 andy-laptop wpa_supplicant[1107]: CTRL-EVENT-SCAN-RESULTS 
Dec  9 12:58:19 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:19 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:21 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:21 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:21 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:22 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:23 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:23 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:24 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:24 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:24 andy-laptop wpa_supplicant[1107]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Dec  9 12:58:25 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:25 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:27 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:27 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:27 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:27 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:28 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:28 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:29 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:29 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:30 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:30 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:32 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:32 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:32 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:33 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:34 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:34 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:35 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:35 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:36 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:36 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:38 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:38 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:38 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:38 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:39 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:39 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:40 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:40 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:41 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> 4-way handshake
Dec  9 12:58:41 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  9 12:58:43 andy-laptop wpa_supplicant[1107]: Associated with 00:0f:b5:ee:3d:8e
Dec  9 12:58:43 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated
Dec  9 12:58:43 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  9 12:58:44 andy-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Dec  9 12:58:44 andy-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec  9 12:58:44 andy-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Dec  9 12:58:44 andy-laptop wpa_supplicant[1107]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec  9 12:58:44 andy-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec  9 12:58:53 andy-laptop wpa_supplicant[1107]: Authentication with 00:00:00:00:00:00 timed out.
Dec  9 12:58:54 andy-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Dec  9 12:58:54 andy-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Saunders)
Dec  9 12:58:54 andy-laptop NetworkManager: <info>  Marking connection 'Auto Saunders' invalid.
Dec  9 12:58:54 andy-laptop NetworkManager: <info>  Activation (wlan0) failed.
Dec  9 12:58:54 andy-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Dec  9 12:58:54 andy-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Dec  9 12:59:09 andy-laptop wpa_supplicant[1107]: CTRL-EVENT-SCAN-RESULTS 

```

What do I need to do in order to connect to WPA networks?

---

