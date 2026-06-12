---
title: "wifi isn't working"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by wifihelp on 2010-04-19
For the past almost year, once in a while my wifi won't work.

At home, I use an ethernet cable. When I go out, or am out of town, about 1/3 times the wifi won't connect, and won't even find access points. Once this happens, no matter how many times I restart, the wifi won't work. The ONLY way I can get it to work again is if I reboot with the ethernet cord plugged into the laptop and into a router/switch/hub. My neighbor (the one who got me into Ubuntu) is a pretty experienced linux network admin who looked a my laptop and has no idea what is causing this. I've attached my syslog log entry for the last time this happened. Does anyone know why this is? I LOVE ubuntu but I may need to switch back to Windows because I NEED wifi to work. 

Any help would be appreciated. 

You will see in the logfile I tried connecting to two different APs. The one that always works is the second one, called linksys.

                                 Syslog:
 ---------------------
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto sammysosa' 
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto sammysosa' has security, but secrets are required.  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto sammysosa' has security, and secrets exist.  No new secrets needed.  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'sammysosa'  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'  
 Apr 19 12:04:07 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed  
 Apr 19 12:04:07 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1  
 Apr 19 12:04:07 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected  
 Apr 19 12:04:10 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning  
 Apr 19 12:04:13 ubuntu wpa_supplicant[1326]: CTRL-EVENT-SCAN-RESULTS  
 Apr 19 12:04:13 ubuntu wpa_supplicant[1326]: WPS-AP-AVAILABLE  
 Apr 19 12:04:13 ubuntu wpa_supplicant[1326]: Trying to associate with 00:14:d1:c0:10:ef (SSID='sammysosa' freq=2437 MHz)  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating  
 Apr 19 12:04:13 ubuntu wpa_supplicant[1326]: Association request to the driver failed  
 Apr 19 12:04:13 ubuntu kernel: [   88.185202] wlan0: authenticate with AP 00:14:d1:c0:10:ef  
 Apr 19 12:04:13 ubuntu kernel: [   88.186992] wlan0: authenticated  
 Apr 19 12:04:13 ubuntu kernel: [   88.186995] wlan0: associate with AP 00:14:d1:c0:10:ef  
 Apr 19 12:04:13 ubuntu kernel: [   88.190963] wlan0: RX AssocResp from 00:14:d1:c0:10:ef (capab=0x431 status=0 aid=19)  
 Apr 19 12:04:13 ubuntu kernel: [   88.190966] wlan0: associated  
 Apr 19 12:04:13 ubuntu wpa_supplicant[1326]: Associated with 00:14:d1:c0:10:ef  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated  
 Apr 19 12:04:13 ubuntu kernel: [   88.195531] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake  
 Apr 19 12:04:13 ubuntu kernel: [   88.203859] wlan0: deauthenticated (Reason: 0)  
 Apr 19 12:04:13 ubuntu wpa_supplicant[1326]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect  
 Apr 19 12:04:13 ubuntu wpa_supplicant[1326]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 3 (reason 0)  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linksys'  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linksys' requires no security.  No secrets needed.  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'linksys'  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1  
 Apr 19 12:04:13 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning  
 Apr 19 12:04:14 ubuntu kernel: [   89.200060] wlan0: direct probe to AP 00:14:d1:c0:10:ef try 1  
 Apr 19 12:04:14 ubuntu kernel: [   89.203520] wlan0 direct probe responded  
 Apr 19 12:04:14 ubuntu kernel: [   89.203525] wlan0: authenticate with AP 00:14:d1:c0:10:ef  
 Apr 19 12:04:14 ubuntu kernel: [   89.205201] wlan0: authenticated  
 Apr 19 12:04:14 ubuntu kernel: [   89.205205] wlan0: associate with AP 00:14:d1:c0:10:ef  
 Apr 19 12:04:14 ubuntu kernel: [   89.208677] wlan0: RX ReassocResp from 00:14:d1:c0:10:ef (capab=0x431 status=0 aid=19)  
 Apr 19 12:04:14 ubuntu kernel: [   89.208679] wlan0: associated  
 Apr 19 12:04:14 ubuntu wpa_supplicant[1326]: No network configuration found for the current AP  
 Apr 19 12:04:14 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated  
 Apr 19 12:04:14 ubuntu kernel: [   89.210470] wlan0: disassociating by local choice (reason=3)  
 Apr 19 12:04:14 ubuntu wpa_supplicant[1326]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys  
 Apr 19 12:04:14 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected  
 Apr 19 12:04:14 ubuntu avahi-daemon[1101]: Registering new address record for fe80::222:faff:fe14:43de on wlan0.*.  
 Apr 19 12:04:23 ubuntu wpa_supplicant[1326]: Authentication with 00:00:00:00:00:00 timed out.  
 Apr 19 12:04:23 ubuntu wpa_supplicant[1326]: Failed to initiate AP scan.  
 Apr 19 12:04:23 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning  
 Apr 19 12:04:23 ubuntu kernel: [   98.656037] wlan0: no IPv6 routers present  
 Apr 19 12:04:30 ubuntu NetworkManager: <info>  wlan0: link timed out.  
 Apr 19 12:04:33 ubuntu wpa_supplicant[1326]: Failed to initiate AP scan.  
 Apr 19 12:05:11 ubuntu wpa_supplicant[1326]: last message repeated 3 times  
 Apr 19 12:05:13 ubuntu wpa_supplicant[1326]: Failed to initiate AP scan.  
 Apr 19 12:05:14 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation.  
 Apr 19 12:05:14 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 11)  
 Apr 19 12:05:14 ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (linksys)  
 Apr 19 12:05:14 ubuntu NetworkManager: <info>  Marking connection 'Auto linksys' invalid.  
 Apr 19 12:05:14 ubuntu NetworkManager: <info>  Activation (wlan0) failed.  
 Apr 19 12:05:14 ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)  
 Apr 19 12:05:14 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).  
 Apr 19 12:05:17 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Julissa'  
 Apr 19 12:05:17 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)

---

### Post by wifihelp on 2010-04-19
I forgot to add that the computer is a Toshiba Satellite A355-S6925 and the wifi card is Intel Wi-Fi Link 5100AGN (802.11a/g/n.

---

