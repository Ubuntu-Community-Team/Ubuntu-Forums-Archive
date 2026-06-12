---
title: "URGENT!  Won't connect half the time to wifi"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by X5-655 on 2010-08-30
I'm about ready to dismiss Ubuntu as a serious distrobution because I've had WAY too many problems with Ubuntu and reliability..

I just spent the past 15 minutes trying to connect to my wifi..  This happens at ANY freakin location..  At one point I even changed the router name and rebooted the router, despite every other device in the home having no problem connect to it.  Look at this log, and look at how it just won't connect to the damn access point..  Now, right now, I'm very frustrated that it took a freakin 15 minutes to connect to Wifi..  At the end of the log, it finally connected..

```
Aug 30 01:04:37 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:04:37 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:04:37 brandon-laptop dhclient: All rights reserved.
Aug 30 01:04:37 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:04:37 brandon-laptop dhclient: 
Aug 30 01:04:37 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:04:37 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:04:37 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:04:37 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:04:39 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Aug 30 01:04:43 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Aug 30 01:04:54 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Aug 30 01:05:12 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Aug 30 01:05:20 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3118
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (linuxrox)
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  Marking connection 'Auto linuxrox' invalid.
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 30 01:05:22 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:05:22 brandon-laptop kernel: [  271.622696] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:05:22 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linuxrox'
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto linuxrox' has security, but secrets are required.
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linuxrox' has security, and secrets exist.  No new secrets needed.
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Config: added 'ssid' value 'linuxrox'
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 30 01:05:40 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:05:40 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 30 01:05:40 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 30 01:05:41 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:05:41 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:05:41 brandon-laptop kernel: [  290.741695] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:05:41 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:05:41 brandon-laptop kernel: [  290.941927] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:05:41 brandon-laptop kernel: [  290.947446] wlan0: direct probe responded
Aug 30 01:05:41 brandon-laptop kernel: [  290.947458] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:05:41 brandon-laptop kernel: [  290.950114] wlan0: authenticated
Aug 30 01:05:41 brandon-laptop kernel: [  290.950157] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:05:41 brandon-laptop kernel: [  290.954111] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:05:41 brandon-laptop kernel: [  290.954120] wlan0: associated
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:05:41 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:05:41 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:05:41 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:22:75:13:55:cf completed (reauth) [id=0 id_str=]
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linuxrox'.
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  dhclient started with pid 3138
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 30 01:05:41 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:05:41 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:05:41 brandon-laptop dhclient: All rights reserved.
Aug 30 01:05:41 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:05:41 brandon-laptop dhclient: 
Aug 30 01:05:41 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:05:41 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:05:41 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:05:41 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:05:43 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Aug 30 01:05:48 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Aug 30 01:06:02 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 30 01:06:07 brandon-laptop anacron[1044]: Job `cron.daily' started
Aug 30 01:06:07 brandon-laptop anacron[3145]: Updated timestamp for job `cron.daily' to 2010-08-30
Aug 30 01:06:09 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3138
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (linuxrox)
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  Marking connection 'Auto linuxrox' invalid.
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 30 01:06:27 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:06:27 brandon-laptop kernel: [  336.622730] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:06:27 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linuxrox'
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto linuxrox' has security, but secrets are required.
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linuxrox' has security, and secrets exist.  No new secrets needed.
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Config: added 'ssid' value 'linuxrox'
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 30 01:06:37 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:06:37 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 30 01:06:37 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 30 01:06:38 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:06:38 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:06:38 brandon-laptop kernel: [  347.701557] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:06:38 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:06:38 brandon-laptop kernel: [  347.900337] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:06:38 brandon-laptop kernel: [  347.905826] wlan0: direct probe responded
Aug 30 01:06:38 brandon-laptop kernel: [  347.905834] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:06:38 brandon-laptop kernel: [  347.907777] wlan0: authenticated
Aug 30 01:06:38 brandon-laptop kernel: [  347.907811] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:06:38 brandon-laptop kernel: [  347.911767] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:06:38 brandon-laptop kernel: [  347.911773] wlan0: associated
Aug 30 01:06:38 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:06:38 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:06:38 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:22:75:13:55:cf completed (reauth) [id=0 id_str=]
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linuxrox'.
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  dhclient started with pid 3173
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 30 01:06:38 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:06:38 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:06:38 brandon-laptop dhclient: All rights reserved.
Aug 30 01:06:38 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:06:38 brandon-laptop dhclient: 
Aug 30 01:06:38 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:06:38 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:06:38 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:06:38 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:06:40 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 30 01:06:47 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Aug 30 01:06:55 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Aug 30 01:07:10 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Aug 30 01:07:11 brandon-laptop NetworkManager: <info>  Sleeping...
Aug 30 01:07:11 brandon-laptop NetworkManager: <info>  (wlan0): now unmanaged
Aug 30 01:07:11 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 1 (reason 37)
Aug 30 01:07:11 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Aug 30 01:07:11 brandon-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3173
Aug 30 01:07:11 brandon-laptop NetworkManager: <info>  (wlan0): cleaning up...
Aug 30 01:07:12 brandon-laptop NetworkManager: <info>  (wlan0): taking down device.
Aug 30 01:07:12 brandon-laptop kernel: [  381.422685] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:07:12 brandon-laptop avahi-daemon[901]: Withdrawing address record for fe80::222:68ff:fe8f:ce80 on wlan0.
Aug 30 01:07:12 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:07:12 brandon-laptop NetworkManager: <info>  (eth0): now unmanaged
Aug 30 01:07:12 brandon-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Aug 30 01:07:12 brandon-laptop NetworkManager: <info>  (eth0): cleaning up...
Aug 30 01:07:12 brandon-laptop NetworkManager: <info>  (eth0): taking down device.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Waking up...
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): now managed
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): bringing up device.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): preparing device.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (eth0): now managed
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (eth0): bringing up device.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (eth0): preparing device.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Aug 30 01:07:23 brandon-laptop kernel: [  392.840402] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 30 01:07:23 brandon-laptop kernel: [  392.843943] r8169: eth0: link down
Aug 30 01:07:23 brandon-laptop kernel: [  392.844522] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 30 01:07:23 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:07:23 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linuxrox'
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linuxrox' has security, and secrets exist.  No new secrets needed.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Config: added 'ssid' value 'linuxrox'
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 30 01:07:23 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:07:23 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 30 01:07:23 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 30 01:07:28 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 30 01:07:29 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:07:29 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:07:29 brandon-laptop kernel: [  398.821185] ath9k: Two wiphys trying to scan at the same time
Aug 30 01:07:29 brandon-laptop kernel: [  398.821262] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:07:29 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:07:29 brandon-laptop kernel: [  399.019393] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:07:29 brandon-laptop kernel: [  399.024921] wlan0: direct probe responded
Aug 30 01:07:29 brandon-laptop kernel: [  399.024933] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:07:29 brandon-laptop kernel: [  399.026912] wlan0: authenticated
Aug 30 01:07:29 brandon-laptop kernel: [  399.026957] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:07:29 brandon-laptop kernel: [  399.030897] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:07:29 brandon-laptop kernel: [  399.030905] wlan0: associated
Aug 30 01:07:29 brandon-laptop kernel: [  399.041151] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 30 01:07:29 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:07:29 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:07:29 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:22:75:13:55:cf completed (auth) [id=0 id_str=]
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linuxrox'.
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  dhclient started with pid 3178
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 30 01:07:29 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:07:29 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:07:29 brandon-laptop dhclient: All rights reserved.
Aug 30 01:07:29 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:07:29 brandon-laptop dhclient: 
Aug 30 01:07:29 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:07:29 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:07:29 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:07:29 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:07:29 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Aug 30 01:07:31 brandon-laptop avahi-daemon[901]: Registering new address record for fe80::222:68ff:fe8f:ce80 on wlan0.*.
Aug 30 01:07:32 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Aug 30 01:07:34 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:07:34 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> 4-way handshake
Aug 30 01:07:34 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:07:34 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:07:37 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Aug 30 01:07:39 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:07:39 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> 4-way handshake
Aug 30 01:07:39 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:07:39 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:07:40 brandon-laptop kernel: [  409.410073] wlan0: no IPv6 routers present
Aug 30 01:07:44 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:07:44 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> 4-way handshake
Aug 30 01:07:44 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:07:44 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:07:49 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Aug 30 01:08:05 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3178
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (linuxrox)
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  Marking connection 'Auto linuxrox' invalid.
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 30 01:08:15 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:08:15 brandon-laptop kernel: [  444.652656] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:08:15 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:08:23 brandon-laptop AptDaemon: INFO: Quiting due to inactivity
Aug 30 01:08:23 brandon-laptop AptDaemon: INFO: Shutdown was requested
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linuxrox'
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto linuxrox' has security, but secrets are required.
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linuxrox' has security, and secrets exist.  No new secrets needed.
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Config: added 'ssid' value 'linuxrox'
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 30 01:08:23 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:08:23 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 30 01:08:23 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:08:23 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:08:23 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:08:23 brandon-laptop kernel: [  453.361182] ath9k: Two wiphys trying to scan at the same time
Aug 30 01:08:23 brandon-laptop kernel: [  453.361234] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:08:24 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:08:24 brandon-laptop kernel: [  453.559608] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:08:24 brandon-laptop kernel: [  453.565170] wlan0: direct probe responded
Aug 30 01:08:24 brandon-laptop kernel: [  453.565181] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:08:24 brandon-laptop kernel: [  453.567185] wlan0: authenticated
Aug 30 01:08:24 brandon-laptop kernel: [  453.567244] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:08:24 brandon-laptop kernel: [  453.571261] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:08:24 brandon-laptop kernel: [  453.571270] wlan0: associated
Aug 30 01:08:24 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:08:24 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:08:24 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:22:75:13:55:cf completed (reauth) [id=0 id_str=]
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linuxrox'.
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  dhclient started with pid 3183
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 30 01:08:24 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:08:24 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:08:24 brandon-laptop dhclient: All rights reserved.
Aug 30 01:08:24 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:08:24 brandon-laptop dhclient: 
Aug 30 01:08:24 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:08:24 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:08:24 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:08:24 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:08:24 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Aug 30 01:08:28 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Aug 30 01:08:37 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Aug 30 01:08:52 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 30 01:08:59 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3183
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (linuxrox)
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  Marking connection 'Auto linuxrox' invalid.
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 30 01:09:09 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:09:09 brandon-laptop kernel: [  498.622759] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:09:09 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:09:16 brandon-laptop NetworkManager: <info>  WiFi now disabled by radio killswitch
Aug 30 01:09:16 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 2 (reason 0)
Aug 30 01:09:16 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:09:16 brandon-laptop avahi-daemon[901]: Withdrawing address record for fe80::222:68ff:fe8f:ce80 on wlan0.
Aug 30 01:09:31 brandon-laptop NetworkManager: <info>  WiFi now enabled by radio killswitch
Aug 30 01:09:31 brandon-laptop NetworkManager: <info>  (wlan0): bringing up device.
Aug 30 01:09:31 brandon-laptop kernel: [  521.170349] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 30 01:09:31 brandon-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 30 01:09:31 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 30 01:09:31 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:09:31 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:09:31 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linuxrox'
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto linuxrox' has security, but secrets are required.
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linuxrox' has security, and secrets exist.  No new secrets needed.
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Config: added 'ssid' value 'linuxrox'
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 30 01:09:42 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:09:42 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 30 01:09:42 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Aug 30 01:09:43 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:09:43 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:09:43 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:09:43 brandon-laptop kernel: [  532.611181] ath9k: Two wiphys trying to scan at the same time
Aug 30 01:09:43 brandon-laptop kernel: [  532.611234] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:09:43 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:09:43 brandon-laptop kernel: [  532.809454] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:09:43 brandon-laptop kernel: [  533.000178] wlan0: direct probe to AP 00:22:75:13:55:cf (try 2)
Aug 30 01:09:43 brandon-laptop kernel: [  533.200156] wlan0: direct probe to AP 00:22:75:13:55:cf (try 3)
Aug 30 01:09:43 brandon-laptop kernel: [  533.205728] wlan0: direct probe responded
Aug 30 01:09:43 brandon-laptop kernel: [  533.205740] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:09:43 brandon-laptop kernel: [  533.220410] wlan0: authenticated
Aug 30 01:09:43 brandon-laptop kernel: [  533.220460] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:09:43 brandon-laptop kernel: [  533.224443] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:09:43 brandon-laptop kernel: [  533.224451] wlan0: associated
Aug 30 01:09:43 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:09:43 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:09:43 brandon-laptop kernel: [  533.234646] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 30 01:09:43 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:09:45 brandon-laptop avahi-daemon[901]: Registering new address record for fe80::222:68ff:fe8f:ce80 on wlan0.*.
Aug 30 01:09:53 brandon-laptop wpa_supplicant[933]: Authentication with 00:22:75:13:55:cf timed out.
Aug 30 01:09:53 brandon-laptop kernel: [  543.300143] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:09:53 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:09:53 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Aug 30 01:09:53 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:09:53 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 30 01:09:53 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 30 01:09:54 brandon-laptop kernel: [  543.420119] wlan0: no IPv6 routers present
Aug 30 01:09:54 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:09:54 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:09:54 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Aug 30 01:09:54 brandon-laptop kernel: [  543.539336] ath9k: Two wiphys trying to scan at the same time
Aug 30 01:09:54 brandon-laptop kernel: [  543.540307] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:09:54 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:09:54 brandon-laptop kernel: [  543.729463] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:09:54 brandon-laptop kernel: [  543.920153] wlan0: direct probe to AP 00:22:75:13:55:cf (try 2)
Aug 30 01:09:54 brandon-laptop kernel: [  544.120158] wlan0: direct probe to AP 00:22:75:13:55:cf (try 3)
Aug 30 01:09:54 brandon-laptop kernel: [  544.320130] wlan0: direct probe to AP 00:22:75:13:55:cf timed out
Aug 30 01:10:04 brandon-laptop wpa_supplicant[933]: Authentication with 00:22:75:13:55:cf timed out.
Aug 30 01:10:04 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Aug 30 01:10:04 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 30 01:10:04 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:10:04 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:10:04 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:10:04 brandon-laptop kernel: [  554.331827] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:10:05 brandon-laptop kernel: [  554.530137] wlan0: direct probe to AP 00:22:75:13:55:cf (try 2)
Aug 30 01:10:05 brandon-laptop kernel: [  554.535660] wlan0: direct probe responded
Aug 30 01:10:05 brandon-laptop kernel: [  554.535671] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:10:05 brandon-laptop kernel: [  554.537608] wlan0: authenticated
Aug 30 01:10:05 brandon-laptop kernel: [  554.537654] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:10:05 brandon-laptop kernel: [  554.541630] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:10:05 brandon-laptop kernel: [  554.541640] wlan0: associated
Aug 30 01:10:05 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:10:05 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:10:05 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:22:75:13:55:cf completed (auth) [id=0 id_str=]
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linuxrox'.
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  dhclient started with pid 3191
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 30 01:10:05 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:10:05 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:10:05 brandon-laptop dhclient: All rights reserved.
Aug 30 01:10:05 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:10:05 brandon-laptop dhclient: 
Aug 30 01:10:05 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:10:05 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:10:05 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:10:05 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:10:06 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 30 01:10:13 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Aug 30 01:10:25 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Aug 30 01:10:40 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3191
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (linuxrox)
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  Marking connection 'Auto linuxrox' invalid.
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 30 01:10:50 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:10:50 brandon-laptop kernel: [  599.630269] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:10:50 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  Sleeping...
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (wlan0): now unmanaged
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 37)
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (wlan0): cleaning up...
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (wlan0): taking down device.
Aug 30 01:11:15 brandon-laptop avahi-daemon[901]: Withdrawing address record for fe80::222:68ff:fe8f:ce80 on wlan0.
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (eth0): now unmanaged
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (eth0): cleaning up...
Aug 30 01:11:15 brandon-laptop NetworkManager: <info>  (eth0): taking down device.
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  Waking up...
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (wlan0): now managed
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (wlan0): bringing up device.
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (wlan0): preparing device.
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (eth0): now managed
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (eth0): bringing up device.
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (eth0): preparing device.
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Aug 30 01:11:52 brandon-laptop kernel: [  662.090421] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 30 01:11:52 brandon-laptop kernel: [  662.094842] r8169: eth0: link down
Aug 30 01:11:52 brandon-laptop kernel: [  662.095545] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 30 01:11:52 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 30 01:11:52 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:11:52 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:12:07 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 2 (reason 0)
Aug 30 01:12:07 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:12:07 brandon-laptop NetworkManager: <info>  (wlan0): taking down device.
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): bringing up device.
Aug 30 01:12:09 brandon-laptop kernel: [  679.150432] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 30 01:12:09 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:12:09 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linuxrox'
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto linuxrox' has security, but secrets are required.
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linuxrox' has security, and secrets exist.  No new secrets needed.
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Config: added 'ssid' value 'linuxrox'
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 30 01:12:09 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:12:09 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 30 01:12:09 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 30 01:12:14 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 30 01:12:15 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:12:15 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:12:15 brandon-laptop kernel: [  685.131202] ath9k: Two wiphys trying to scan at the same time
Aug 30 01:12:15 brandon-laptop kernel: [  685.131285] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:12:15 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:12:15 brandon-laptop kernel: [  685.329471] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:12:15 brandon-laptop kernel: [  685.335012] wlan0: direct probe responded
Aug 30 01:12:15 brandon-laptop kernel: [  685.335022] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:12:15 brandon-laptop kernel: [  685.337072] wlan0: authenticated
Aug 30 01:12:15 brandon-laptop kernel: [  685.337132] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:12:15 brandon-laptop kernel: [  685.341190] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:12:15 brandon-laptop kernel: [  685.341199] wlan0: associated
Aug 30 01:12:15 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:12:15 brandon-laptop kernel: [  685.351757] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:12:15 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:12:15 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:22:75:13:55:cf completed (auth) [id=0 id_str=]
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linuxrox'.
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  dhclient started with pid 3201
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 30 01:12:15 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 30 01:12:15 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:12:15 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:12:15 brandon-laptop dhclient: All rights reserved.
Aug 30 01:12:15 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:12:15 brandon-laptop dhclient: 
Aug 30 01:12:16 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:12:16 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:12:16 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:12:16 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:12:17 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Aug 30 01:12:17 brandon-laptop avahi-daemon[901]: Registering new address record for fe80::222:68ff:fe8f:ce80 on wlan0.*.
Aug 30 01:12:20 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:12:20 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> 4-way handshake
Aug 30 01:12:20 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:12:20 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:12:22 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 30 01:12:25 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:12:25 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> 4-way handshake
Aug 30 01:12:25 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:12:25 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:12:26 brandon-laptop kernel: [  696.270036] wlan0: no IPv6 routers present
Aug 30 01:12:29 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Aug 30 01:12:30 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:12:30 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> 4-way handshake
Aug 30 01:12:30 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:12:30 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:12:40 brandon-laptop kernel: [  709.980082] usb 1-6: new high speed USB device using ehci_hcd and address 4
Aug 30 01:12:40 brandon-laptop kernel: [  710.132569] usb 1-6: configuration #1 chosen from 1 choice
Aug 30 01:12:40 brandon-laptop kernel: [  710.204729] Initializing USB Mass Storage driver...
Aug 30 01:12:40 brandon-laptop kernel: [  710.205033] scsi2 : SCSI emulation for USB Mass Storage devices
Aug 30 01:12:40 brandon-laptop kernel: [  710.205214] usbcore: registered new interface driver usb-storage
Aug 30 01:12:40 brandon-laptop kernel: [  710.205225] USB Mass Storage support registered.
Aug 30 01:12:40 brandon-laptop kernel: [  710.206776] usb-storage: device found at 4
Aug 30 01:12:40 brandon-laptop kernel: [  710.206783] usb-storage: waiting for device to settle before scanning
Aug 30 01:12:42 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Aug 30 01:12:45 brandon-laptop kernel: [  715.200415] usb-storage: device scan complete
Aug 30 01:12:45 brandon-laptop kernel: [  715.201115] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2
Aug 30 01:12:45 brandon-laptop kernel: [  715.202108] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug 30 01:12:45 brandon-laptop kernel: [  715.205418] sd 2:0:0:0: [sdb] 8001165 512-byte logical blocks: (4.09 GB/3.81 GiB)
Aug 30 01:12:45 brandon-laptop kernel: [  715.205896] sd 2:0:0:0: [sdb] Write Protect is off
Aug 30 01:12:45 brandon-laptop kernel: [  715.205904] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
Aug 30 01:12:45 brandon-laptop kernel: [  715.205910] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Aug 30 01:12:45 brandon-laptop kernel: [  715.209038] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Aug 30 01:12:45 brandon-laptop kernel: [  715.209053]  sdb: sdb1
Aug 30 01:12:45 brandon-laptop kernel: [  715.215336] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Aug 30 01:12:45 brandon-laptop kernel: [  715.215347] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Aug 30 01:12:53 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 3201
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (linuxrox)
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  Marking connection 'Auto linuxrox' invalid.
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 30 01:13:01 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:13:01 brandon-laptop kernel: [  730.622731] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:13:01 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 30 01:14:14 brandon-laptop kernel: [  803.582126] usb 1-6: USB disconnect, address 4
Aug 30 01:14:36 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 2 (reason 0)
Aug 30 01:14:36 brandon-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 30 01:14:36 brandon-laptop NetworkManager: <info>  (wlan0): taking down device.
Aug 30 01:14:36 brandon-laptop avahi-daemon[901]: Withdrawing address record for fe80::222:68ff:fe8f:ce80 on wlan0.
Aug 30 01:14:39 brandon-laptop NetworkManager: <info>  (wlan0): bringing up device.
Aug 30 01:14:39 brandon-laptop kernel: [  828.563242] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 30 01:14:39 brandon-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 30 01:14:39 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 30 01:14:39 brandon-laptop wpa_supplicant[933]: Failed to initiate AP scan.
Aug 30 01:14:39 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linuxrox'
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto linuxrox' has security, but secrets are required.
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linuxrox' has security, and secrets exist.  No new secrets needed.
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Config: added 'ssid' value 'linuxrox'
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 30 01:14:45 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:14:45 brandon-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 30 01:14:45 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Aug 30 01:14:46 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:14:46 brandon-laptop wpa_supplicant[933]: Trying to associate with 00:22:75:13:55:cf (SSID='linuxrox' freq=2437 MHz)
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 30 01:14:46 brandon-laptop kernel: [  835.581191] ath9k: Two wiphys trying to scan at the same time
Aug 30 01:14:46 brandon-laptop kernel: [  835.581273] wlan0: deauthenticating from 00:22:75:13:55:cf by local choice (reason=3)
Aug 30 01:14:46 brandon-laptop wpa_supplicant[933]: WPS-AP-AVAILABLE 
Aug 30 01:14:46 brandon-laptop kernel: [  835.782017] wlan0: direct probe to AP 00:22:75:13:55:cf (try 1)
Aug 30 01:14:46 brandon-laptop kernel: [  835.787544] wlan0: direct probe responded
Aug 30 01:14:46 brandon-laptop kernel: [  835.787556] wlan0: authenticate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:14:46 brandon-laptop kernel: [  835.790100] wlan0: authenticated
Aug 30 01:14:46 brandon-laptop kernel: [  835.790153] wlan0: associate with AP 00:22:75:13:55:cf (try 1)
Aug 30 01:14:46 brandon-laptop kernel: [  835.794116] wlan0: RX AssocResp from 00:22:75:13:55:cf (capab=0x411 status=0 aid=1)
Aug 30 01:14:46 brandon-laptop kernel: [  835.794125] wlan0: associated
Aug 30 01:14:46 brandon-laptop wpa_supplicant[933]: Associated with 00:22:75:13:55:cf
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 30 01:14:46 brandon-laptop kernel: [  835.804720] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 30 01:14:46 brandon-laptop wpa_supplicant[933]: WPA: Key negotiation completed with 00:22:75:13:55:cf [PTK=CCMP GTK=TKIP]
Aug 30 01:14:46 brandon-laptop wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:22:75:13:55:cf completed (auth) [id=0 id_str=]
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linuxrox'.
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  dhclient started with pid 3288
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 30 01:14:46 brandon-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 30 01:14:46 brandon-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 30 01:14:46 brandon-laptop dhclient: All rights reserved.
Aug 30 01:14:46 brandon-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 01:14:46 brandon-laptop dhclient: 
Aug 30 01:14:46 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 30 01:14:46 brandon-laptop dhclient: Listening on LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:14:46 brandon-laptop dhclient: Sending on   LPF/wlan0/00:22:68:8f:ce:80
Aug 30 01:14:46 brandon-laptop dhclient: Sending on   Socket/fallback
Aug 30 01:14:47 brandon-laptop avahi-daemon[901]: Registering new address record for fe80::222:68ff:fe8f:ce80 on wlan0.*.
Aug 30 01:14:49 brandon-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 30 01:14:49 brandon-laptop dhclient: DHCPOFFER of 172.24.1.12 from 172.24.1.2
Aug 30 01:14:49 brandon-laptop dhclient: DHCPREQUEST of 172.24.1.12 on wlan0 to 255.255.255.255 port 67
Aug 30 01:14:49 brandon-laptop dhclient: DHCPACK of 172.24.1.12 from 172.24.1.2
Aug 30 01:14:49 brandon-laptop dhclient: bound to 172.24.1.12 -- renewal in 321750 seconds.
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>    address 172.24.1.12
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>    prefix 16 (255.255.0.0)
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>    gateway 172.24.1.1
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>    nameserver '172.24.1.2'
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 30 01:14:49 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 30 01:14:49 brandon-laptop avahi-daemon[901]: Joining mDNS multicast group on interface wlan0.IPv4 with address 172.24.1.12.
Aug 30 01:14:49 brandon-laptop avahi-daemon[901]: New relevant interface wlan0.IPv4 for mDNS.
Aug 30 01:14:49 brandon-laptop avahi-daemon[901]: Registering new address record for 172.24.1.12 on wlan0.IPv4.
Aug 30 01:14:50 brandon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Aug 30 01:14:50 brandon-laptop NetworkManager: <info>  Policy set 'Auto linuxrox' (wlan0) as default for routing and DNS.
Aug 30 01:14:50 brandon-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Aug 30 01:14:50 brandon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 30 01:14:49 brandon-laptop ntpdate[3331]: step time server 91.189.94.4 offset -1.520729 sec
Aug 30 01:14:54 brandon-laptop kernel: [  845.812522] wlan0: no IPv6 routers present
```

---

### Post by X5-655 on 2010-08-31
Well once again, Debian guys helped me out, and not a single sole here cared.

They pointed out that by the logs, network manager seems to forget it's supposed to be using a wpa key...

Using a different wifi manager now, and not a single problem.

---

### Post by DavidOfLondon on 2010-08-31
> **X5-655 said:**
> Well once again, Debian guys helped me out, and not a single sole here cared.

They pointed out that by the logs, network manager seems to forget it's supposed to be using a wpa key...

Using a different wifi manager now, and not a single problem.
I share your disappointment. This place can be very self-interested....I'm finding this to be the case with a gigantic percentage of long-term snotty linux users.

If their system works fine they don't give a hoot if yours does.

My only piece of advice - now that you've got an answer edit your post with ####EDIT at the top and write up briefly how you fixed it. Be different to all those socially-backward types who don't care; someone else will need this info of yours soon and if you edit your post it'll come up when they google the problem :-)

Best,

David.

---

