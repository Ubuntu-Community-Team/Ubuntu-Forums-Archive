---
title: "Ath9k from compat-wireless--total bust"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by Viola00 on 2009-11-21
so i had the ath928 working fine a while ago compat but now its just giving me a horrible time. right now ive got compat-wireless 2.6.31-rc7... i think... btw im running 9.10 64bit with 2.6.31-14.... when i try to connect:

```


Nov 21 18:02:09 gavin-lx NetworkManager: Unhandled setting property type (write) 'ipv6/dns' : 'GPtrArray_GArray_guchar__'
Nov 21 18:02:09 gavin-lx NetworkManager: Unhandled setting property type (write) 'ipv6/addresses' : 'GPtrArray_GValueArray_GArray_guchar_+guint__'
Nov 21 18:02:09 gavin-lx NetworkManager: Unhandled setting property type (write) 'ipv6/routes' : 'GPtrArray_GValueArray_GArray_guchar_+guint+GArray_guchar_+guint__'
Nov 21 18:02:10 gavin-lx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Alice-53444145'
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Alice-53444145' has security, and secrets exist.  No new secrets needed.
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Config: added 'ssid' value 'Alice-53444145'
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov 21 18:02:10 gavin-lx NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 21 18:02:10 gavin-lx NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  Config: set interface ap_scan to 1
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 21 18:02:10 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:02:14 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 18:02:14 gavin-lx wpa_supplicant[1630]: WPS-AP-AVAILABLE 
Nov 21 18:02:14 gavin-lx wpa_supplicant[1630]: Trying to associate with 00:25:53:09:37:48 (SSID='Alice-53444145' freq=2412 MHz)
Nov 21 18:02:14 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 21 18:02:15 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 18:02:15 gavin-lx wpa_supplicant[1630]: WPS-AP-AVAILABLE 
Nov 21 18:02:15 gavin-lx wpa_supplicant[1630]: Associated with 00:25:53:09:37:48
Nov 21 18:02:15 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 21 18:02:15 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 21 18:02:20 gavin-lx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Nov 21 18:02:23 gavin-lx wpa_supplicant[1630]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Nov 21 18:02:23 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 18:02:23 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Nov 21 18:02:23 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:02:25 gavin-lx wpa_supplicant[1630]: Authentication with 00:00:00:00:00:00 timed out.
Nov 21 18:02:25 gavin-lx wpa_supplicant[1630]: Failed to initiate AP scan.
Nov 21 18:02:25 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 21 18:02:25 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:02:26 gavin-lx NetworkManager: <info>  wlan0: link timed out.
Nov 21 18:02:27 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 18:02:27 gavin-lx wpa_supplicant[1630]: WPS-AP-AVAILABLE 
Nov 21 18:02:27 gavin-lx wpa_supplicant[1630]: Trying to associate with 00:25:53:09:37:48 (SSID='Alice-53444145' freq=2412 MHz)
Nov 21 18:02:27 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 21 18:02:27 gavin-lx wpa_supplicant[1630]: Associated with 00:25:53:09:37:48
Nov 21 18:02:27 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 21 18:02:27 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 21 18:02:35 gavin-lx wpa_supplicant[1630]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Nov 21 18:02:35 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 18:02:35 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Nov 21 18:02:35 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:02:37 gavin-lx wpa_supplicant[1630]: Authentication with 00:00:00:00:00:00 timed out.
Nov 21 18:02:37 gavin-lx wpa_supplicant[1630]: Failed to initiate AP scan.
Nov 21 18:02:37 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 21 18:02:37 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:02:39 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 18:02:39 gavin-lx wpa_supplicant[1630]: WPS-AP-AVAILABLE 
Nov 21 18:02:39 gavin-lx wpa_supplicant[1630]: Trying to associate with 00:25:53:09:37:48 (SSID='Alice-53444145' freq=2412 MHz)
Nov 21 18:02:39 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 21 18:02:39 gavin-lx wpa_supplicant[1630]: Associated with 00:25:53:09:37:48
Nov 21 18:02:39 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 21 18:02:39 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 21 18:02:41 gavin-lx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov 21 18:02:48 gavin-lx wpa_supplicant[1630]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Nov 21 18:02:48 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 18:02:48 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Nov 21 18:02:48 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:02:49 gavin-lx dhclient: No DHCPOFFERS received.
Nov 21 18:02:49 gavin-lx dhclient: No working leases in persistent database - sleeping.
Nov 21 18:02:49 gavin-lx wpa_supplicant[1630]: Authentication with 00:00:00:00:00:00 timed out.
Nov 21 18:02:49 gavin-lx wpa_supplicant[1630]: Failed to initiate AP scan.
Nov 21 18:02:49 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 21 18:02:49 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:02:51 gavin-lx NetworkManager: <info>  wlan0: link timed out.
Nov 21 18:02:52 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 18:02:52 gavin-lx wpa_supplicant[1630]: WPS-AP-AVAILABLE 
Nov 21 18:02:52 gavin-lx wpa_supplicant[1630]: Trying to associate with 00:25:53:09:37:48 (SSID='Alice-53444145' freq=2412 MHz)
Nov 21 18:02:52 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 21 18:02:52 gavin-lx wpa_supplicant[1630]: Associated with 00:25:53:09:37:48
Nov 21 18:02:52 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 21 18:02:52 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 21 18:03:00 gavin-lx wpa_supplicant[1630]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Nov 21 18:03:00 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 18:03:00 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Nov 21 18:03:00 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:03:02 gavin-lx wpa_supplicant[1630]: Authentication with 00:00:00:00:00:00 timed out.
Nov 21 18:03:02 gavin-lx wpa_supplicant[1630]: Failed to initiate AP scan.
Nov 21 18:03:02 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 21 18:03:02 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 21 18:03:04 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 18:03:04 gavin-lx wpa_supplicant[1630]: WPS-AP-AVAILABLE 
Nov 21 18:03:04 gavin-lx wpa_supplicant[1630]: Trying to associate with 00:25:53:09:37:48 (SSID='Alice-53444145' freq=2412 MHz)
Nov 21 18:03:04 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 21 18:03:04 gavin-lx wpa_supplicant[1630]: Associated with 00:25:53:09:37:48
Nov 21 18:03:04 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 21 18:03:04 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Alice-53444145' has security, but secrets are required.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 21 18:03:11 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Alice-53444145' has security, but secrets are required.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Alice-53444145' has security, but secrets are required.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Alice-53444145' has security, but secrets are required.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) failed for access point (Alice-53444145)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Marking connection 'Auto Alice-53444145' invalid.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) failed.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Nov 21 18:03:11 gavin-lx NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Nov 21 18:03:11 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 18:03:14 gavin-lx wpa_supplicant[1630]: Authentication with 00:00:00:00:00:00 timed out.
Nov 21 18:03:26 gavin-lx wpa_supplicant[1630]: CTRL-EVENT-SCAN-RESULTS 



```

---

