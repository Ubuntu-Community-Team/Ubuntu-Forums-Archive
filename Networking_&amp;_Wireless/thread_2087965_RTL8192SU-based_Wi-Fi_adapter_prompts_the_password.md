---
title: "RTL8192SU-based Wi-Fi adapter prompts the password repeatedly"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by leventov on 2012-11-25
[_Still_]("http://askubuntu.com/questions/90350/rtl8192su-based-wi-fi-adapter-disconnects-permanently"). I tried to apply commands from [_this thread_]("http://ubuntuforums.org/showthread.php?t=2021493"), blacklisted iwl3945 in a nutshell, and network manager started to prompt the password instead silent of reconnecting.
[FONT="Courier New"]
$ uname -a
Linux ubuntu 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[/FONT]
Log:
[FONT="Courier New"]
Nov 25 12:26:50 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 25 12:26:50 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 25 12:26:50 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete. <--  wireless connection finally established, 7 minutes of proper internet :)
Nov 25 12:33:48 ubuntu wpa_supplicant[1828]: wlan0: WPA: Group rekeying completed with 00:25:12:86:a2:64 [GTK=TKIP]
Nov 25 12:33:56 ubuntu wpa_supplicant[1828]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:25:12:86:a2:64 reason=0
Nov 25 12:33:56 ubuntu NetworkManager[1181]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 25 12:33:56 ubuntu NetworkManager[1181]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 25 12:34:06 ubuntu wpa_supplicant[1828]: wlan0: Trying to associate with 00:25:12:86:a2:64 (SSID='My Place' freq=2437 MHz)
Nov 25 12:34:06 ubuntu wpa_supplicant[1828]: wlan0: Association request to the driver failed
Nov 25 12:34:06 ubuntu NetworkManager[1181]: <info> (wlan0): supplicant interface state: scanning -> associating
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <warn> (wlan0): link timed out.
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <info> (wlan0): device state change: activated -> failed (reason 'supplicant-timeout') [100 120 11]
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <warn> Activation (wlan0) failed for connection 'My Place'
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 25 12:34:11 ubuntu wpa_supplicant[1828]: wlan0: Authentication with 00:25:12:86:a2:64 timed out.
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2800
Nov 25 12:34:11 ubuntu avahi-daemon[1184]: Withdrawing address record for fe80::214:d1ff:fe6c:5219 on wlan0.
Nov 25 12:34:11 ubuntu avahi-daemon[1184]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::214:d1ff:fe6c:5219.
Nov 25 12:34:11 ubuntu avahi-daemon[1184]: Interface wlan0.IPv6 no longer relevant for mDNS.
Nov 25 12:34:11 ubuntu avahi-daemon[1184]: Withdrawing address record for 192.168.1.4 on wlan0.
Nov 25 12:34:11 ubuntu avahi-daemon[1184]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Nov 25 12:34:11 ubuntu kernel: [  494.449508] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <warn> DNS: plugin dnsmasq update failed
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <info> ((null)): removing resolv.conf from /sbin/resolvconf
Nov 25 12:34:11 ubuntu avahi-daemon[1184]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <info> (wlan0): supplicant interface state: associating -> disconnected
Nov 25 12:34:11 ubuntu NetworkManager[1181]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 25 12:34:12 ubuntu NetworkManager[1181]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Auto-activating connection 'My Place'.
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) starting connection 'My Place'
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0/wireless): access point 'My Place' has security, but secrets are required.
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0/wireless): connection 'My Place' has security, and secrets exist.  No new secrets needed.
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Config: added 'ssid' value 'My Place'
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Config: added 'scan_ssid' value '1'
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Config: added 'psk' value '<omitted>'
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> Config: set interface ap_scan to 1
Nov 25 12:34:14 ubuntu NetworkManager[1181]: <info> (wlan0): supplicant interface state: inactive -> scanning
[/FONT]

---

