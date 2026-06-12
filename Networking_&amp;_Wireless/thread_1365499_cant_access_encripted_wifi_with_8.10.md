---
title: "cant access encripted wifi with 8.10"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by n-alexander on 2009-12-27
Hello!

1. set up my laptop to access my Wifi router with no security other than MAC filtering on the router - works fine

2. trying to set up WPA with pre-shared key now, using TKIP and ASCII pass phrase, 64bit

3. laptop connects and gets IP from the router, sets the router as default gateway, and for a few seconds I can serf the Internet

4. the router says
> Dec 27 17:48:35 wlan0: A wireless client is associated - 00:16:EB:13:C8:8C
Dec 27 17:48:35 wlan0: WPA-TKIP PSK authentication in progress... 
Dec 27 17:48:35 wlan0: Open and authenticated 

this suggests that I at least configured both devices in the same way.

5. after a few seconds, the laptop looses connection, /var/log/syslog says something like this:

> NetworkManager: <info> Activation (wlan0) Stage 5 of 5 (IP configure commit) complete.


A few seconds passes during which I have IP, gateway, and access. Then:

> wpa_supplicant[776]: CTRL-EVENT-SCAN-RESULTS
wpa_supplicant[776]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
kernel: wlan0: disassociated (Reason: 14)
kernel: wlan0: deauthenticated (Reason: 6)


then it tries to re-associate, but

> kernel: wlan0: AP denied association (code=12)

and this is it. I googled for the reasons, but unsuccessfully.

Help?

---

