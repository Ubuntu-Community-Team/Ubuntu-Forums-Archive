---
title: "Association request to the driver failed"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2012-01-18
Here's my setup: Dell Studio 1555 with Broadcom BCM4312 wireless chip. I'm using Ubuntu 11.10
From time and especially when I leave my connection idle it drops! 
It can last for about an hour without any traffic. Than it drops.
When I have a constant traffic it can stay connected throughout the whole day. 
Here's what I found today in the logs:
```
 Jan 18 13:12:40 bsotirov-Studio-1555 wpa_supplicant[1179]: WPA: Group rekeying completed with 00:21:29:7a:bb:f2 [GTK=CCMP]
Jan 18 13:17:01 bsotirov-Studio-1555 CRON[16283]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 18 14:04:11 bsotirov-Studio-1555 wpa_supplicant[1179]: WPA: Group rekeying completed with 00:21:29:7a:bb:f2 [GTK=CCMP]
Jan 18 14:08:13 bsotirov-Studio-1555 kernel: [20703.461755] indicator-weath[1900] general protection ip:7f9f174f0226 sp:7fff4a598c40 error:0 in libdbusmenu-glib.so.4.0.5[7f9f174e6000+17000]
Jan 18 14:17:01 bsotirov-Studio-1555 CRON[12890]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 18 14:55:42 bsotirov-Studio-1555 wpa_supplicant[1179]: WPA: Group rekeying completed with 00:21:29:7a:bb:f2 [GTK=CCMP]
Jan 18 14:57:40 bsotirov-Studio-1555 wpa_supplicant[1179]: CTRL-EVENT-DISCONNECTED bssid=00:21:29:7a:bb:f2 reason=0
Jan 18 14:57:40 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: completed -> disconnected
Jan 18 14:57:40 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jan 18 14:57:40 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:57:40 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:57:40 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:57:43 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): roamed from BSSID 00:21:29:7A:BB:F2 (prostor) to (none) ((none))
Jan 18 14:57:45 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:57:45 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:57:46 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:57:46 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:57:46 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:57:51 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:57:51 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:57:51 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:57:51 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:57:51 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <warn> (eth1): link timed out.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): deactivating device (reason 'supplicant-timeout') [11]
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): canceled DHCP transaction, DHCP client pid 3721
Jan 18 14:57:55 bsotirov-Studio-1555 avahi-daemon[1125]: Withdrawing address record for 192.168.3.100 on eth1.
Jan 18 14:57:55 bsotirov-Studio-1555 avahi-daemon[1125]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.3.100.
Jan 18 14:57:55 bsotirov-Studio-1555 avahi-daemon[1125]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> disconnected
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Auto-activating connection 'prostor'.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) starting connection 'prostor'
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1/wireless): access point 'prostor' has security, but secrets are required.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1/wireless): connection 'prostor' has security, and secrets exist.  No new secrets needed.
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'ssid' value 'prostor'
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'scan_ssid' value '1'
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'psk' value '<omitted>'
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan 18 14:57:55 bsotirov-Studio-1555 dbus[1081]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: set interface ap_scan to 1
Jan 18 14:57:55 bsotirov-Studio-1555 dbus[1081]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 18 14:57:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jan 18 14:57:56 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:57:56 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:57:56 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:01 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:01 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:06 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:06 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:06 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:11 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:11 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:12 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:12 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:12 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:17 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:17 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:17 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:17 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:17 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:22 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:22 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:22 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:22 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:22 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:27 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:27 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:27 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:27 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:27 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:32 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:32 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:33 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:33 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:33 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:38 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:38 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:38 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:38 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:38 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:43 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:43 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:43 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:43 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:43 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:48 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:48 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:49 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:49 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:49 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:54 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 14:58:54 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 14:58:54 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 14:58:54 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 14:58:54 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 14:58:55 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1/wireless): association took too long.
Jan 18 14:58:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 18 14:58:55 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1/wireless): asking for new secrets
Jan 18 14:58:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> disconnected
Jan 18 14:58:55 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan 18 15:00:55 bsotirov-Studio-1555 NetworkManager[1142]: <warn> No agents were available for this request.
Jan 18 15:00:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan 18 15:00:55 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1) failed for access point (prostor)
Jan 18 15:00:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> Marking connection 'prostor' invalid.
Jan 18 15:00:55 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1) failed.
Jan 18 15:00:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 18 15:00:55 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): deactivating device (reason 'none') [0]
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Auto-activating connection 'prostor'.
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) starting connection 'prostor'
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1/wireless): access point 'prostor' has security, but secrets are required.
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1/wireless): connection 'prostor' has security, and secrets exist.  No new secrets needed.
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'ssid' value 'prostor'
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'scan_ssid' value '1'
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: added 'psk' value '<omitted>'
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> Config: set interface ap_scan to 1
Jan 18 15:06:19 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jan 18 15:06:20 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:20 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:20 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:06:25 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:06:25 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:06:25 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:25 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:25 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:06:30 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:06:30 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:06:30 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:30 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:30 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:06:35 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:06:35 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:06:36 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:36 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:36 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:06:41 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:06:41 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:06:41 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:41 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:41 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:06:46 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:06:46 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:06:46 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:46 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:46 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:06:51 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:06:51 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:06:52 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:52 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:52 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:06:57 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:06:57 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:06:57 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:06:57 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:06:57 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:07:02 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:07:02 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:07:02 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:07:02 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:07:02 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:07:07 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:07:07 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:07:07 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:07:07 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:07:07 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:07:12 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:07:12 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:07:13 bsotirov-Studio-1555 wpa_supplicant[1179]: Trying to associate with 00:21:29:7a:bb:f2 (SSID='prostor' freq=2432 MHz)
Jan 18 15:07:13 bsotirov-Studio-1555 wpa_supplicant[1179]: Association request to the driver failed
Jan 18 15:07:13 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> associating
Jan 18 15:07:18 bsotirov-Studio-1555 wpa_supplicant[1179]: Authentication with 00:21:29:7a:bb:f2 timed out.
Jan 18 15:07:18 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: associating -> scanning
Jan 18 15:07:20 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1/wireless): association took too long.
Jan 18 15:07:20 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 18 15:07:20 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1/wireless): asking for new secrets
Jan 18 15:07:20 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan 18 15:07:20 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan 18 15:07:23 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): supplicant interface state: scanning -> inactive
Jan 18 15:07:25 bsotirov-Studio-1555 NetworkManager[1142]: <warn> No agents were available for this request.
Jan 18 15:07:25 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan 18 15:07:25 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1) failed for access point (prostor)
Jan 18 15:07:25 bsotirov-Studio-1555 NetworkManager[1142]: <info> Marking connection 'prostor' invalid.
Jan 18 15:07:25 bsotirov-Studio-1555 NetworkManager[1142]: <warn> Activation (eth1) failed.
Jan 18 15:07:25 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 18 15:07:25 bsotirov-Studio-1555 NetworkManager[1142]: <info> (eth1): deactivating device (reason 'none') [0] 
```

After the last rekeying at 14:55 I've got disconnected. Than this message appears again and again:
"Association request to the driver failed". During that time I've got the authentication window asking me for the SSID password again and again. And no matter that I enter it correctly, it doesn't authenticate.
I've seen in the forums that this message unfortunately isn't conclusive. Does anybody has a clue?
The only way I know so far to recover from this situation is to reboot.

---

### Post by lz1dsb on 2012-01-26
I can't really believe that I'm the only one experiencing this... Hm... the Broadcom chips seem quite popular on the laptops these days.

---

### Post by lz1dsb on 2012-01-28
Just an observation I made recently. The connection tend to drop more often when there's almost zero traffic over the wireless interface. If I leave my laptop connected for about an hour and there's no constant traffic the connection usually breaks.

---

### Post by kevdog on 2012-01-28
A little more info would be helpful.  Like driver you are using.

---

### Post by adampaetznick on 2012-01-30
Similar problem here.  The main symptom is an unreliable network connection.

syslog contains a number of messages like:
```

Jan 30 11:51:14 wpa_supplicant[1095]: Trying to associate with 00:0b:86:3f:ff:41 (SSID='eduroam' freq=2412 MHz)
Jan 30 11:51:14 wpa_supplicant[1095]: Association request to the driver failed

```

Here is my lspci output:
```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Broadcom Corporation Device 04b5
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f5200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 31-a7-56-ff-ff-b7-00-25
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, ssb
```

---

### Post by chili555 on 2012-01-30
> Kernel driver in use: wl
	Kernel modules: wl, ssbkevdog is probably wondering if there is a conflict here. Is ssb really loaded?```
lsmod | grep -e b4 -e ssb
```It may be required for your ethernet device. We also wonder if it's actually a power management issue. Let's see:```
iwconfig
```Is your wireless interface eth1? Does it help to do:```
sudo iwconfig eth1 power off
```'Power' in this case actually refers to power management; as in "Go to sleep if Adam is not using the wireless."

---

### Post by lz1dsb on 2012-01-31
I'll check this and post outputs from my machine. I'm on the road and my laptop is at home but I switched it off and I don't have a remote access...

---

### Post by lz1dsb on 2012-02-05
Here are the outputs from my machine:
```
bsotirov@bsotirov-Studio-1555:~$ lspci -k
bsotirov@bsotirov-Studio-1555:~$ 04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
				 Subsystem: Dell Wireless 1397 WLAN Mini-Card
				 Kernel driver in use: wl
				 Kernel modules: wl, ssb
```
```
bsotirov@bsotirov-Studio-1555:~$ lsmod | grep -e b4 -e ssb
bsotirov@bsotirov-Studio-1555:~$ 
```
```
bsotirov@bsotirov-Studio-1555:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:198  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```
I'm right now connected to the wireless access point and I'm submitting this message over the wireless interface. Why is 'iwconfig' showing that I'm  'Not-Associated'. Is it because the Network Manager application is controlling my wireless card?

---

### Post by lz1dsb on 2012-02-05
Just to add that the wireless connection is pretty stable while I have active traffic over the wireless interface. When I leave my machine with an internet radio running it stays stable for the whole day without a glitch... When the connection is idle though it's up and running only for about an hour and so.
Why would a constant traffic over the interface matter?

---

### Post by lz1dsb on 2012-10-22
I now use D-link's DWA-131 which is perfectly compatible with Linux...

---

