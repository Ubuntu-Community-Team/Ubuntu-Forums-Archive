---
title: "Wireless and then no wireless after a few minutes."
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by gonenowhere on 2013-01-07
SO I just installed 12.04lts at first the wireless was working and then I did the update seemed to be working fine updated my nvidia graphics card seems to be fine after a couple minutes it just stopped. So I produced what I think is a wireless log here:

an  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0/wireless): access point 'Buck you fitch' has security, but secrets are required.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0/wireless): connection 'Buck you fitch' has security, and secrets exist.  No new secrets needed.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'ssid' value 'Buck you fitch'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'scan_ssid' value '1'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'auth_alg' value 'OPEN'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: added 'psk' value '<omitted>'
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  7 08:58:33 WTF NetworkManager[799]: <info> Config: set interface ap_scan to 1
Jan  7 08:58:33 WTF NetworkManager[799]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  7 08:58:40 WTF NetworkManager[799]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  7 08:59:33 WTF NetworkManager[799]: <warn> Activation (wlan0/wireless): association took too long.
Jan  7 08:59:33 WTF NetworkManager[799]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  7 08:59:33 WTF NetworkManager[799]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan  7 08:59:33 WTF NetworkManager[799]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  7 08:59:33 WTF NetworkManager[799]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.



If you need anything else let me know I am a little lost here but it seems to be getting stuck authenticating maybe? I am new to wifi driver issues. Any help is greatly apppreciated.

---

### Post by gonenowhere on 2013-01-07
Im thinking this may be an issue with the new network manager because it does not seem to happen until after I update my new install of ubuntu 12.04.

Im going to reinstall and see if that works without updating.

---

