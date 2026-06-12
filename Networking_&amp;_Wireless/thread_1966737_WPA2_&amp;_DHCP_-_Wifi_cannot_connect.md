---
title: "WPA2 &amp; DHCP - Wifi cannot connect"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by derekcentrico on 2012-04-27
Recently, I ran into problems with WiFi on my Ubuntu laptop.  I have the Intel Ultimate-N 6300 WiFi chip.  Around February, it stopped connecting after installing a slew of updates to Ubuntu 11.10 x86.  I did an upgrade to 12.04 x86 and this did not fix anything.  So, I formatted and went to x64 just for fun.  Still, nothing works.

I found that I can get on WiFi so long as I manually set an IP address instead of using DHCP if I want to connect a protected network (WPA2 Personal is in use).  However, I can connect to an open network and obtain IP information from DHCP without a problem.  The issue lies in WPA + DHCP.

Here's a log snippet from 11.10 x86 I believe...things are running together from toying with this last night.

```
pr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) starting connection 'dgaptwifi'
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1/wireless): access point 'dgaptwifi' has security, but secrets are required.
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Apr 26 17:07:33 DG-Lenovo-Ubuntu kernel: [   76.843091] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr 26 17:07:33 DG-Lenovo-Ubuntu kernel: [   76.843095] cfg80211: Restoring regulatory settings
Apr 26 17:07:33 DG-Lenovo-Ubuntu kernel: [   76.843132] cfg80211: Calling CRDA to update world regulatory domain
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Apr 26 17:07:33 DG-Lenovo-Ubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1/wireless): connection 'dgaptwifi' has security, and secrets exist.  No new secrets needed.
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Config: added 'ssid' value 'dgaptwifi'
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Config: added 'scan_ssid' value '1'
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Config: added 'psk' value '<omitted>'
Apr 26 17:07:33 DG-Lenovo-Ubuntu NetworkManager[1074]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Apr 26 17:07:33 DG-Lenovo-Ubuntu wpa_supplicant[1161]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3

```
 
Any help would be appreciated.  Thanks!

---

