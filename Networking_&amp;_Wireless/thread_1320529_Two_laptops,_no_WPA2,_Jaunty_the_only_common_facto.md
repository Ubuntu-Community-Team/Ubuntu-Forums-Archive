---
title: "Two laptops, no WPA2, Jaunty the only common factor"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by caliston on 2009-11-09
I have two laptops that I'm trying to connect to a WPA2 network.

Laptop #1 is a Toshiba Portege M200 with an IPW2200:
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05).  It uses the ipw2200 driver.

WPA2 worked just fine in Hardy, to the same network, but has never worked since I installed Jaunty.  It also worked fine in XP.

Laptop #2 is a Dell Mini 9 with a Broadcom BCM4312 (rev 01).  I think WPA2 also worked fine in XP but I can't remember if I tested it.  It uses the closed-source Broadcom driver (think it might be called 'wl', but I'm not sure)

Both are on up-to-date jaunty, 2.6.28-16-generic, 32 bit.  Both have modules like this loaded (from #2):
```

ieee80211_crypt_tkip   16896  0
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

```

#1 uses WICD in plain Ubuntu, #2 uses NetworkManager in UNR.  (I've tried both on both machines, with no difference).

The access point is a Debian etch/MIPS box with an Atheros wireless card with the madwifi drivers.  There are two wireless networks exported by the card, one configured as WEP and the other as WPA and WPA2 using hostap, using both AES and TKIP.  The hostap configuration is attached (with most of the extraneous comments deleted).

When I try to connect from #2, NetworkManager offers me the only option of 'WPA & WPA2 Personal'.  I set the password to the key directly copied out of /etc/hostap/wpa_psk on the server (without the preceding 00:00:00:00:00:00 and whitespace).  I've attached the syslog, which isn't too helpful.  There's no output in dmesg.

The accesspoint log (in verbose mode) looks like this (repeated over and over again):
```

Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 IEEE 802.11: associated
Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 WPA: event 1 notification
Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 WPA: start authentication
Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 IEEE 802.1X: unauthorizing port
Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 WPA: no PSK configured for the STA
Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 IEEE 802.1X: unauthorizing port
Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 IEEE 802.11: deauthenticated due to lo
cal deauth request
Nov  9 15:22:21 devonian hostapd: ath1: STA 00:24:d2:41:62:97 IEEE 802.11: disassociated

```

While I'm attempting to configure, iwconfig just says 'Access Point: Not Associated' - it never picks up the name of the WPA AP.

Any suggestions?  I can always ramp up the debugging options on the AP if that's of use.

---

