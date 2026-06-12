---
title: "wpa supplicant error"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by jcastilow on 2009-03-16
Hi, I can no longer connect to my school's wireless. This is the system log, any suggestions?

Mar 12 23:14:08 jacob-laptop NetworkManager: <info> (wlan0): supplicant connection state change: 3 -> 0 
Mar 12 23:14:08 jacob-laptop NetworkManager: <info> (wlan0): supplicant connection state change: 0 -> 2 
Mar 12 23:14:09 jacob-laptop NetworkManager: <info> (wlan0): supplicant connection state change: 2 -> 3 
Mar 12 23:14:09 jacob-laptop kernel: [161532.852651] wlan0: authenticate with AP 00:0b:0e:4f:26:82
Mar 12 23:14:09 jacob-laptop kernel: [161533.052059] wlan0: authenticate with AP 00:0b:0e:4f:26:82
Mar 12 23:14:09 jacob-laptop kernel: [161533.252829] wlan0: authenticate with AP 00:0b:0e:4f:26:82
Mar 12 23:14:10 jacob-laptop kernel: [161533.452724] wlan0: authentication with AP 00:0b:0e:4f:26:82 timed out
Mar 12 23:14:13 jacob-laptop NetworkManager: <info> Activation (wlan0/wireless): association took too long. 
Mar 12 23:14:13 jacob-laptop NetworkManager: <info> (wlan0): device state change: 5 -> 6 
Mar 12 23:14:13 jacob-laptop NetworkManager: <info> Activation (wlan0/wireless): asking for new secrets 
Mar 12 23:14:13 jacob-laptop NetworkManager: <info> (wlan0): supplicant connection state change: 3 -> 0 
Mar 12 23:14:28 jacob-laptop NetworkManager: <info> wlan0: link timed out. 
Mar 12 23:14:52 jacob-laptop NetworkManager: <info> (wlan0): supplicant connection state change: 0 -> 2 
Mar 12 23:15:34 jacob-laptop NetworkManager: <WARN> get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Mar 12 23:15:34 jacob-laptop NetworkManager: <info> (wlan0): device state change: 6 -> 9 
Mar 12 23:15:34 jacob-laptop NetworkManager: <info> Activation (wlan0) failed for access point (resnet) 
Mar 12 23:15:34 jacob-laptop NetworkManager: <info> Marking connection 'resnet' invalid. 
Mar 12 23:15:34 jacob-laptop NetworkManager: <info> Activation (wlan0) failed. 
Mar 12 23:15:34 jacob-laptop NetworkManager: <info> (wlan0): device state change: 9 -> 3 
Mar 12 23:15:34 jacob-laptop NetworkManager: <info> (wlan0): deactivating device (reason: 0).

---

