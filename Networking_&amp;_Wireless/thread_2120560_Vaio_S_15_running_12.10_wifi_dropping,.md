---
title: "Vaio S 15 running 12.10 wifi dropping,"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by vitriolix on 2013-02-26
I've been having a problem with my new Sony Vaio S 15 getting dropped from my home wireless.  When it happens my internet drops but I can still login to the router (192.168.1.1)... if I look in the log on the router I see messages like this:

kernel: eth1: received packet with  own address as source address
kernel: eth2: received packet with  own address as source address

It takes a couple minutes, then my network will start working again.  Sometimes this will happen 10-20 times a day, usually when I'm on a video conference call ;)

The router is an Asus RT-N66U.

I'm running Ubuntu 12.10 with all the latest updates.

Very frustrating and I'm kind of at a loss what to do.

A strange wrinkle, no other device on this network causes this, and this laptop never has this trouble on any other network I've noticed.

Any help is appreciated.

---

### Post by vitriolix on 2013-03-02
Just happened again and i checked the syslog on my ubuntu box:

  1 21:05:07 stealth NetworkManager[1231]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar  1 21:05:07 stealth NetworkManager[1231]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar  1 21:05:18 stealth ntpdate[14760]: step time server 91.189.94.4 offset 0.910029 sec
Mar  1 21:05:59 stealth wpa_supplicant[1569]: wlan0: SME: Trying to authenticate with 50:46:5d:6d:69:08 (SSID='xiphoid' freq=2412 MHz)
Mar  1 21:05:59 stealth NetworkManager[1231]: <info> (wlan0): supplicant interface state: completed -> authenticating
Mar  1 21:05:59 stealth kernel: [ 5088.969827] wlan0: authenticate with 50:46:5d:6d:69:08
Mar  1 21:05:59 stealth kernel: [ 5088.970463] wlan0: send auth to 50:46:5d:6d:69:08 (try 1/3)
Mar  1 21:05:59 stealth wpa_supplicant[1569]: wlan0: Trying to associate with 50:46:5d:6d:69:08 (SSID='xiphoid' freq=2412 MHz)
Mar  1 21:05:59 stealth kernel: [ 5088.977090] wlan0: authenticated
Mar  1 21:05:59 stealth kernel: [ 5088.977232] wlan0: waiting for beacon from 50:46:5d:6d:69:08
Mar  1 21:05:59 stealth NetworkManager[1231]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar  1 21:06:00 stealth kernel: [ 5089.079491] wlan0: associate with 50:46:5d:6d:69:08 (try 1/3)
Mar  1 21:06:00 stealth kernel: [ 5089.092782] wlan0: RX AssocResp from 50:46:5d:6d:69:08 (capab=0x411 status=0 aid=6)
Mar  1 21:06:00 stealth kernel: [ 5089.095342] wlan0: associated
Mar  1 21:06:00 stealth wpa_supplicant[1569]: wlan0: Associated with 50:46:5d:6d:69:08
Mar  1 21:06:00 stealth NetworkManager[1231]: <info> (wlan0): supplicant interface state: associating -> associated
Mar  1 21:06:00 stealth NetworkManager[1231]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Mar  1 21:06:00 stealth wpa_supplicant[1569]: wlan0: WPA: Key negotiation completed with 50:46:5d:6d:69:08 [PTK=CCMP GTK=CCMP]
Mar  1 21:06:00 stealth wpa_supplicant[1569]: wlan0: CTRL-EVENT-CONNECTED - Connection to 50:46:5d:6d:69:08 completed (reauth) [id=0 id_str=]
Mar  1 21:06:00 stealth NetworkManager[1231]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Mar  1 21:06:00 stealth NetworkManager[1231]: <info> (wlan0): roamed from BSSID BC:AE:C5:AF:FE:54 (xiphoid) to 50:46:5D:6D:69:08 (xiphoid)

Doesn't mean much to me but maybe something will stand out to someone here?

---

### Post by vitriolix on 2013-03-04
For posterity... I disabled the 5ghz on my router, I'm thinking this might be caused by my laptop switching from 2.4ghz to 5ghz and back... we'll see

---

