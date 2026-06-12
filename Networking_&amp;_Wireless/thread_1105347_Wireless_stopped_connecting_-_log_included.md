---
title: "Wireless stopped connecting - log included"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by xirrin on 2009-03-24
When I first installed Ubuntu I couldn't get the wireless card to connect at all. I found a posting somewhere on the forum here that gave me a command to log what was happening to try and debug it. As soon as I ran that command it connected and I didn't need to go ask any questions. Well, now after about 2 weeks of it working just fine I was trying to make an adjustment to the GUI and was following some instructions. One of the steps was to hit CTRL+ALT+BACKSPACE. I did that, and when GNOME loaded again, the problem was back. I kept the command though to log things, and this is what I've got. Any ideas?

```
Mar 24 15:11:34 ewhbuntu NetworkManager: <WARN>  nm_device_wifi_set_enabled(): not in expected unavailable state! 
Mar 24 15:11:34 ewhbuntu NetworkManager: <info>  (wlan1): bringing up device. 
Mar 24 15:11:34 ewhbuntu NetworkManager: <info>  (wlan1): device state change: 2 -> 3 
Mar 24 15:11:34 ewhbuntu NetworkManager: <info>  (wlan1): supplicant interface state change: 1 -> 2. 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1) starting connection 'Auto ewlan' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  (wlan1): device state change: 3 -> 4 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  (wlan1): device state change: 4 -> 5 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1/wireless): connection 'Auto ewlan' has security, and secrets exist.  No new secrets needed. 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: added 'ssid' value 'ewlan' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 2 -> 0 
Mar 24 15:11:56 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 0 -> 2 
Mar 24 15:12:01 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 2 -> 3 
Mar 24 15:12:01 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 3 -> 4 
Mar 24 15:12:01 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:02 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:02 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:03 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:03 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:04 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:04 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:05 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:05 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:06 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:06 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:07 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:07 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:08 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:08 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:09 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:09 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:11 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:11 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:11 ewhbuntu NetworkManager: <info>  wlan1: link timed out. 
Mar 24 15:12:12 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:12 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:13 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:13 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:14 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:14 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:15 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:15 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:16 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:16 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:17 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:17 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:18 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:18 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:19 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:19 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:20 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:20 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:22 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:22 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:30 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:30 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:31 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:31 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:32 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:32 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:33 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:33 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:34 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:34 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:35 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:35 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:36 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:36 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:37 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:37 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:38 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:38 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:40 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:40 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:41 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:42 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:43 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:44 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:45 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:45 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:46 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:46 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:47 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:47 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:48 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:48 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:49 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:49 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:51 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:51 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:52 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:52 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:53 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:53 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:54 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:54 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:55 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 4 
Mar 24 15:12:55 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 4 -> 5 
Mar 24 15:12:56 ewhbuntu NetworkManager: <info>  Activation (wlan1/wireless): association took too long. 
Mar 24 15:12:56 ewhbuntu NetworkManager: <info>  (wlan1): device state change: 5 -> 6 
Mar 24 15:12:56 ewhbuntu NetworkManager: <info>  Activation (wlan1/wireless): asking for new secrets 
Mar 24 15:12:56 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 5 -> 0 
Mar 24 15:13:04 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 0 -> 2 
Mar 24 15:13:05 ewhbuntu NetworkManager: <info>  (wlan1): supplicant connection state change: 2 -> 0 
Mar 24 15:13:11 ewhbuntu NetworkManager: <info>  wlan1: link timed out. 
Mar 24 15:13:24 ewhbuntu NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Mar 24 15:13:24 ewhbuntu NetworkManager: <info>  (wlan1): device state change: 6 -> 9 
Mar 24 15:13:24 ewhbuntu NetworkManager: <info>  Activation (wlan1) failed for access point (ewlan) 
Mar 24 15:13:24 ewhbuntu NetworkManager: <info>  Marking connection 'Auto ewlan' invalid. 
Mar 24 15:13:24 ewhbuntu NetworkManager: <info>  Activation (wlan1) failed. 
Mar 24 15:13:24 ewhbuntu NetworkManager: <info>  (wlan1): device state change: 9 -> 3 
Mar 24 15:13:24 ewhbuntu NetworkManager: <info>  (wlan1): deactivating device (reason: 0). 
```

---

### Post by xirrin on 2009-03-25
Bump! This is getting really annoying running a CAT5 cable all the way across my apartment for this when it has been working for the last 2 weeks. :(

---

### Post by xirrin on 2009-03-25
Well, after much messing with everything I decided to try and troubleshoot it from the router side of things even though 4 other wireless devices were connecting fine to it. After playing around for a while I changed the wireless security protocal to Auto WPA&WPA2 instead of forcing WPA Only. Oddly enough, even though my wireless card in my computer does not support WPA2 - it connected immediately. Go figure.

---

