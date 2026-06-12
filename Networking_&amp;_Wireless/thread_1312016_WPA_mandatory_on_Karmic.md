---
title: "WPA mandatory on Karmic?"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by ivancruz on 2009-11-02
After a fresh install of Karmic on an HP laptop I could not get my wireless to work with my router configured to use WEP security. An windows XP installed on the same machine managed to connect flawlessly. I could also connect Karmic to the open wireless network of my neighbor.

To make things even more strange, I could see an IP allocated to the laptop HMAC on the router logs. After dealing with dmesg, iwconfig and many other commands I tried to follow messages on syslog while a connection was being attempted. Thats an extract of the pertinent messages:

```
Nov  2 21:35:30 ubuntu kernel: [ 1440.020090] b43-phy0: Radio hardware status changed to ENABLED
Nov  2 21:35:30 ubuntu NetworkManager: <info>  Wireless now enabled by radio killswitch
Nov  2 21:35:30 ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Nov  2 21:35:30 ubuntu kernel: [ 1440.184081] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov  2 21:35:30 ubuntu kernel: [ 1440.224521] Registered led device: b43-phy0::radio
Nov  2 21:35:30 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Nov  2 21:35:30 ubuntu kernel: [ 1440.236410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  2 21:35:31 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Nov  2 21:35:31 ubuntu wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 21:35:31 ubuntu wpa_supplicant[1118]: WPS-AP-AVAILABLE 
Nov  2 21:35:31 ubuntu wpa_supplicant[1118]: Failed to initiate AP scan.
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'MindivasNET'
Nov  2 21:35:31 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  2 21:35:31 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'MindivasNET' has security, and secrets exist.  No new secrets needed.
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'MindivasNET'
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Nov  2 21:35:31 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  2 21:35:31 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  2 21:35:31 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Nov  2 21:35:31 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov  2 21:35:36 ubuntu wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 21:35:36 ubuntu kernel: [ 1445.741280] wlan0: authenticate with AP 00:1c:f0:66:1b:1a
Nov  2 21:35:36 ubuntu wpa_supplicant[1118]: WPS-AP-AVAILABLE 
Nov  2 21:35:36 ubuntu wpa_supplicant[1118]: Trying to associate with 00:1c:f0:66:1b:1a (SSID='MindivasNET' freq=2447 MHz)
Nov  2 21:35:36 ubuntu wpa_supplicant[1118]: Association request to the driver failed
Nov  2 21:35:36 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Nov  2 21:35:36 ubuntu kernel: [ 1445.940071] wlan0: authenticate with AP 00:1c:f0:66:1b:1a
Nov  2 21:35:36 ubuntu kernel: [ 1446.140090] wlan0: authenticate with AP 00:1c:f0:66:1b:1a
Nov  2 21:35:36 ubuntu wpa_supplicant[1118]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  2 21:35:36 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Nov  2 21:35:36 ubuntu kernel: [ 1446.340079] wlan0: authentication with AP 00:1c:f0:66:1b:1a timed out
Nov  2 21:35:41 ubuntu wpa_supplicant[1118]: Authentication with 00:00:00:00:00:00 timed out.
Nov  2 21:35:41 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  2 21:35:42 ubuntu wpa_supplicant[1118]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 21:35:42 ubuntu wpa_supplicant[1118]: WPS-AP-AVAILABLE 
Nov  2 21:35:42 ubuntu wpa_supplicant[1118]: Trying to associate with 00:1c:f0:66:1b:1a (SSID='MindivasNET' freq=2447 MHz)
Nov  2 21:35:42 ubuntu wpa_supplicant[1118]: Association request to the driver failed
Nov  2 21:35:42 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov  2 21:35:42 ubuntu kernel: [ 1452.168957] wlan0: authenticate with AP 00:1c:f0:66:1b:1a
Nov  2 21:35:42 ubuntu kernel: [ 1452.368076] wlan0: authenticate with AP 00:1c:f0:66:1b:1a
Nov  2 21:35:42 ubuntu kernel: [ 1452.568070] wlan0: authenticate with AP 00:1c:f0:66:1b:1a
Nov  2 21:35:43 ubuntu wpa_supplicant[1118]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  2 21:35:43 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Nov  2 21:35:43 ubuntu kernel: [ 1452.768070] wlan0: authentication with AP 00:1c:f0:66:1b:1a timed out
Nov  2 21:35:46 ubuntu NetworkManager: <info>  wlan0: link timed out.
Nov  2 21:35:47 ubuntu wpa_supplicant[1118]: Authentication with 00:00:00:00:00:00 timed out.

```

What catch my attention was the many references to "wpa_supplicant". A wpa supplicant was not supposed to be necessary on a WEP connection, am I correct?

So, I went to the router configuration page and changed wireless security to WPA2, tried Karmic again and voilá!!! Everything works. Including that post!!!

So my question is: is WPA mandatory on Karmic? Is it properly documented/announced? Or was it just my fault?

Ivan.

---

### Post by Dark_Stang on 2009-11-02
It isn't manditory, as far as I know, because I'm still able to connect to WEP networks just fine. I recommend sticking with WPA for obvious security reasons, and a nice performance boost, but you may want to investigate this a little.

It looks like you're using the b43 driver for your broadcom card. Have you tried using broadcom's STA driver?

---

### Post by ivancruz on 2009-11-03
There is a Win2K machine on my network with no WPA support at all, thats the reason I am stuck with WEP.

Anyway I am still curious about that wpa supplicant thing on my logs. Was that my fault? There is something I can configure to avoid wpa supplicant interfering?

Ivan.

---

