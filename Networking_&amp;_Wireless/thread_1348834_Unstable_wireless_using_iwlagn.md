---
title: "Unstable wireless using iwlagn"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by lodahl on 2009-12-07
Hi,
I have some problems with my Intel Wireless WiFi Link 5100.

[LEFT]I can get connected, but after about one minute I loose connection again. Then on again after appr. one minute.

My wireless network runs unstable when I'm connected (says my missus).

My Kern.log looks like this
[FONT=Courier New]Dec  7 22:40:38 leif-laptop kernel: [ 1454.069168] wlan0: authenticate with AP 00:02:72:4d:e1:ba
Dec  7 22:40:38 leif-laptop kernel: [ 1454.071159] wlan0: authenticated
Dec  7 22:40:38 leif-laptop kernel: [ 1454.071165] wlan0: associate with AP 00:02:72:4d:e1:ba
Dec  7 22:40:38 leif-laptop kernel: [ 1454.073858] wlan0: RX AssocResp from 00:02:72:4d:e1:ba (capab=0x411 status=12 aid=2)
Dec  7 22:40:38 leif-laptop kernel: [ 1454.073864] wlan0: AP denied association (code=12)
Dec  7 22:40:38 leif-laptop kernel: [ 1454.268061] wlan0: associate with AP 00:02:72:4d:e1:ba
Dec  7 22:40:38 leif-laptop kernel: [ 1454.270333] wlan0: RX AssocResp from 00:02:72:4d:e1:ba (capab=0x411 status=12 aid=2)
Dec  7 22:40:38 leif-laptop kernel: [ 1454.270339] wlan0: AP denied association (code=12)
Dec  7 22:40:38 leif-laptop kernel: [ 1454.468059] wlan0: associate with AP 00:02:72:4d:e1:ba
Dec  7 22:40:38 leif-laptop kernel: [ 1454.470201] wlan0: RX AssocResp from 00:02:72:4d:e1:ba (capab=0x411 status=12 aid=2)
Dec  7 22:40:38 leif-laptop kernel: [ 1454.470207] wlan0: AP denied association (code=12)
Dec  7 22:40:39 leif-laptop kernel: [ 1454.668058] wlan0: association with AP 00:02:72:4d:e1:ba timed out[/FONT]

And it just goes around in circles.

Deamon.log says:[FONT=Courier New]
Dec  7 22:42:34 leif-laptop wpa_supplicant[862]: WPS-AP-AVAILABLE 
Dec  7 22:42:34 leif-laptop wpa_supplicant[862]: Trying to associate with 00:02:72:4d:e1:ba (SSID='lhadol' freq=2412 MHz)
Dec  7 22:42:34 leif-laptop wpa_supplicant[862]: Association request to the driver failed
Dec  7 22:42:34 leif-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  7 22:42:35 leif-laptop wpa_supplicant[862]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec  7 22:42:35 leif-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  7 22:42:39 leif-laptop wpa_supplicant[862]: Authentication with 00:00:00:00:00:00 timed out.
Dec  7 22:42:39 leif-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  7 22:42:42 leif-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Dec  7 22:42:42 leif-laptop wpa_supplicant[862]: WPS-AP-AVAILABLE 
Dec  7 22:42:42 leif-laptop wpa_supplicant[862]: Trying to associate with 00:02:72:4d:e1:ba (SSID='lhadol' freq=2412 MHz)
Dec  7 22:42:42 leif-laptop wpa_supplicant[862]: Association request to the driver failed
Dec  7 22:42:42 leif-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec  7 22:42:43 leif-laptop wpa_supplicant[862]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec  7 22:42:43 leif-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec  7 22:42:47 leif-laptop wpa_supplicant[862]: Authentication with 00:00:00:00:00:00 timed out.
Dec  7 22:42:47 leif-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  7 22:42:47 leif-laptop NetworkManager: <info>  wlan0: link timed out.
Dec  7 22:42:51 leif-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS [/FONT]

I have tried to use, but I can't find a Windowsdriver that can be accepted (vaious errors). Can anyone help me?

The missus is doesn't like a LAN wire go through the living room.


[/LEFT]

---

