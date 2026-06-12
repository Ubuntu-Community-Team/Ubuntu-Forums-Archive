---
title: "Wlan terribly unreliable (3945ABG card)"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by nrthguy on 2011-02-07
So my setup is the following,  I have maverick, and using the network manager that was bundled with the system, haven't changed any settings etc. (was like this with previous versions too)

My AP is a D-Link ADSL Router, WPA2 Only, G Only (54 Mbps); My adaptor in my laptop has a built in Intel® PRO/Wireless 3945ABG.

The router is in the hall, signal has to go through a couple of walls but they're not brick. In fact when I use windows I never have the reception problems I'm going to describe.

I get disconnected every few minutes, especially if the machine is idling, now writing this i was disconnected and reconnected 3 times already. It seems it's easier for it to reconnect if i use the physical wireless switch on the laptop, toggle, then select my AP from the menu in the panel.

I've noticed it's especially bad when my house-mate has his machine on, it has a very similar wireless chip model, and the angle between us both and the router is quite sharp. 
He's using windows and my theory is that the win drivers are more aggressive "somehow".

Here's what I get in daemon.log (some of it anyway, need more?):

```
Feb  7 15:20:16  NetworkManager[918]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Feb  7 15:20:16  NetworkManager[918]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Feb  7 15:20:16  NetworkManager[918]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb  7 15:20:16  NetworkManager[918]: <info> Config: set interface ap_scan to 1
Feb  7 15:20:16  NetworkManager[918]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Feb  7 15:20:19  wpa_supplicant[1037]: Trying to associate with <my ap's MAC> (SSID='mynet' freq=2427 MHz)
Feb  7 15:20:19  NetworkManager[918]: <info> (wlan0): supplicant connection state:  scanning -> associating
Feb  7 15:20:29  wpa_supplicant[1037]: Authentication with <my ap's MAC> timed out.
...
Feb  7 15:18:40  NetworkManager[918]: <warn> (wlan0): link timed out.
Feb  7 15:18:44  NetworkManager[918]: <warn> Activation (wlan0/wireless): association took too long.
Feb  7 15:18:44  NetworkManager[918]: <info> (wlan0): device state change: 5 -> 9 (reason 7)
Feb  7 15:18:44  NetworkManager[918]: <warn> Activation (wlan0) failed for access point (mynet)
Feb  7 15:18:44  NetworkManager[918]: <info> Marking connection 'mynet' invalid.
Feb  7 15:18:44  NetworkManager[918]: <warn> Activation (wlan0) failed.
Feb  7 15:18:44  NetworkManager[918]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Feb  7 15:18:44  NetworkManager[918]: <info> (wlan0): deactivating device (reason: 0).
```

Is anything that can be tweaked so roaming is more aggressive or whatever, lower some threshold just as long it doesn't drop the connection entirely?

Bandwidth isn't concerned, as long as I'm connected the net is as fast as it should be.

---

