---
title: "network manager can't connect due to link timed out"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by bsipos on 2010-04-08
Hi,

I'm experiencing connection problem when I try to connect to a network with my laptop. I'm using ubuntu 10.4 the wireless card is Intel Corporation Wireless WiFi Link 5300 and I'm using the iwlagn modul.

That is what I see in the syslog:

```

NetworkManager: <info>  Activation (wlan0) starting connection 'visitor'
NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (wlan0/wireless): access point 'Ornl-visitor' has security, but secrets are required.
NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 1 802-1x
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (wlan0/wireless): connection 'Visitor' requires no security.  No secrets needed.
NetworkManager: <info>  Config: added 'ssid' value 'visitor'
NetworkManager: <info>  Config: added 'scan_ssid' value '1'
NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Config: set interface ap_scan to 1
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
wpa_supplicant[945]: Failed to initiate AP scan.
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  wlan0: link timed out.
NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation.
NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 11)
NetworkManager: <info>  Activation (wlan0) failed for access point (ornl-visitor)
NetworkManager: <info>  Marking connection 'Visitor' invalid.
NetworkManager: <info>  Activation (wlan0) failed.
NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

```

If I tried to set the network using iwconfig, it managed to set any kind of essid except the right one. When I tried to set the right one, it was always replaced by a long weird string.

Once I stopped the networkmanager, the I could connect.

Has anybody experienced anything similar?
Any ideas?

Thanks

Sipi

---

### Post by nukedathlonman on 2010-04-30
Same issue... But I have a Broadcom 4322 and using the Broadcom STA driver. Still researching, but a bump here might be in order - hopefully someone else is having this problem and or know of a fix.  Going to check the bug tracker, possibly start one.

---

### Post by nukedathlonman on 2010-04-30
I've filed a bug on Launch pad - based on your syslog and my syslog, I think there a bug somewhere in NetworkManager or wpa_supplicant: [https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777)

---

