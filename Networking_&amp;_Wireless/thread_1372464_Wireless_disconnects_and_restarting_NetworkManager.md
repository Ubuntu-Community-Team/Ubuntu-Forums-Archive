---
title: "Wireless disconnects and restarting NetworkManager solves the problem"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by bahsouna on 2010-01-04
Hello

I already checked these 3 topics. But I think that my problem is quite different.

    [http://ubuntuforums.org/showthread.php?t=1314340](http://ubuntuforums.org/showthread.php?t=1314340)
    [http://ubuntuforums.org/showthread.php?t=1367393](http://ubuntuforums.org/showthread.php?t=1367393)
    [http://ubuntuforums.org/showthread.php?t=1353199](http://ubuntuforums.org/showthread.php?t=1353199)

The fact is that I let my laptop switched on to download some stuff while I am at work. I managed to access my laptop remotely using mldonkey web interface. My laptop often disconnects after few hours (sometimes after one hour or two).

I am connected on wireless. I'm using Ubuntu 9.10

```
bahsouna@bahsouna:~$ lspci |grep Network
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

The laptop disconnected around 10am. Here is an extract from daemon.log around 10am

```

Jan  4 10:00:36 bahsouna wpa_supplicant[1105]: CTRL-EVENT-SCAN-RESULTS
Jan  4 10:00:42 bahsouna wpa_supplicant[1105]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  4 10:00:42 bahsouna NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jan  4 10:00:42 bahsouna NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  4 10:00:43 bahsouna wpa_supplicant[1105]: CTRL-EVENT-SCAN-RESULTS
Jan  4 10:00:58 bahsouna wpa_supplicant[1105]: last message repeated 2 times
Jan  4 10:00:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Jan  4 10:00:58 bahsouna NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Jan  4 10:00:58 bahsouna NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan  4 10:00:58 bahsouna avahi-daemon[950]: Withdrawing address record for 192.168.1.18 on wlan0.
Jan  4 10:00:58 bahsouna avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.18.
Jan  4 10:00:58 bahsouna avahi-daemon[950]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0) starting connection 'Auto globalnet_BA'
Jan  4 10:00:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  4 10:00:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto globalnet_BA' has security, and secrets exist.  No new secrets needed.
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Config: added 'ssid' value 'globalnet_BA'
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan  4 10:00:58 bahsouna NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  4 10:00:58 bahsouna NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  4 10:00:58 bahsouna NetworkManager: <info>  Config: set interface ap_scan to 1
Jan  4 10:00:58 bahsouna NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan  4 10:01:00 bahsouna NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  4 10:01:01 bahsouna wpa_supplicant[1105]: CTRL-EVENT-SCAN-RESULTS
Jan  4 10:01:13 bahsouna wpa_supplicant[1105]: last message repeated 2 times
Jan  4 10:01:13 bahsouna NetworkManager: <info>  wlan0: link timed out.
Jan  4 10:01:17 bahsouna wpa_supplicant[1105]: CTRL-EVENT-SCAN-RESULTS
Jan  4 10:01:58 bahsouna wpa_supplicant[1105]: last message repeated 8 times
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto globalnet_BA' has security, but secrets are required.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto globalnet_BA' has security, but secrets are required.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto globalnet_BA' has security, but secrets are required.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto globalnet_BA' has security, but secrets are required.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) failed for access point (globalnet_BA)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Marking connection 'Auto globalnet_BA' invalid.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) failed.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jan  4 10:01:58 bahsouna NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jan  4 10:02:31 bahsouna wpa_supplicant[1105]: CTRL-EVENT-SCAN-RESULTS
Jan  4 10:04:31 bahsouna wpa_supplicant[1105]: CTRL-EVENT-SCAN-RESULTS
Jan  4 10:06:31 bahsouna wpa_supplicant[1105]: CTRL-EVENT-SCAN-RESULTS

```

Please let me now if you need extra information.

EDIT: when i restart NetworkManager ( $ sudo killall NetworkManager ), I can reconnect.

---

### Post by bahsouna on 2010-01-05
Up!

---

