---
title: "Trendnet TEW-424UB USB wireless adapter not working in adhoc mode"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by m83 on 2010-07-14
Hello.

I'm trying to make an adhoc wireless network between an laptop and a desktop computer (that has the Trendnet TEW-424UB USB wireless adapter to one of the USB ports).

The USB adapter is recognized and configured and I guess it works ok when you try to connect to an Access Point (I don't have a wireless router around so I can't confirm this, but lsusb lists the adapter and in syslog everything looks ok).

Now, I'm trying to setup a wireless adhoc network between the desktop computer and the laptop (as the desktop doesn't have 2 ethernet adapters). Everything looks OK on the laptop, but on the desktop I see the following messages in syslog:
```
Jul 14 22:51:25 shade-desktop wpa_supplicant[844]: Authentication with 00:00:00:00:00:00 timed out.
Jul 14 22:51:25 shade-desktop wpa_supplicant[844]: Trying to associate with SSID 'adhoc'
Jul 14 22:51:25 shade-desktop wpa_supplicant[844]: Failed to set operating mode
Jul 14 22:51:25 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 14 22:51:25 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 22:51:25 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 14 22:51:31 shade-desktop NetworkManager: <info>  wlan0: link timed out.
Jul 14 22:51:35 shade-desktop wpa_supplicant[844]: Authentication with 00:00:00:00:00:00 timed out.
Jul 14 22:51:35 shade-desktop wpa_supplicant[844]: Trying to associate with SSID 'adhoc'
Jul 14 22:51:35 shade-desktop wpa_supplicant[844]: Failed to set operating mode
Jul 14 22:51:35 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 14 22:51:35 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 22:51:35 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 14 22:51:45 shade-desktop wpa_supplicant[844]: Authentication with 00:00:00:00:00:00 timed out.
Jul 14 22:51:45 shade-desktop wpa_supplicant[844]: Trying to associate with SSID 'adhoc'
Jul 14 22:51:45 shade-desktop wpa_supplicant[844]: Failed to set operating mode
Jul 14 22:51:45 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul 14 22:51:45 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 22:51:45 shade-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul 14 22:51:46 shade-desktop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.

```

From that, I can conclude that the wireless driver can't set the operating mode on the USB adapter to work in adhoc mode. Is there something wrong with the driver, or I made a mistake somewhere?

Any sugestions on what to do next? Try ndiswrapper maybe (I would prefer not to, as my head is already spinning from troubleshooting this problem and frankly I'm kind of scared of ndiswrapper and what it might do to me :) ).

---

