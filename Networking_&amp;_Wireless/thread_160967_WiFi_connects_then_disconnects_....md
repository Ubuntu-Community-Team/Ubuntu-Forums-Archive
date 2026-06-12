---
title: "WiFi connects then disconnects ..."
date: 2006-04-16
forum: Networking &amp; Wireless
---

### Post by donr on 2006-04-16
I have a problem where wpa_supplicant connects, then disconntects, then connects, ...

I just set up a Linksys WRT54G and have a laptop with an Atheros board.
They are both set to WPA-PSK, SSID broadcast is off,

Here is the wpa_supplicant output (with SSID redacted)
> ioctl[SIOCSIWPMKSA]: Operation not supported
Trying to associate with 00:14:bf:84:b2:a4 (SSID='__SSID__' freq=2447 MHz)
Associated with 00:14:bf:84:b2:a4
WPA: Key negotiation completed with 00:14:bf:84:b2:a4 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:14:bf:84:b2:a4 completed (auth)
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:14:bf:84:b2:a4 (SSID='__SSID__' freq=2447 MHz)
...

With the -dd option I see:
> CTRL-EVENT-CONNECTED - Connection to 00:14:bf:84:b2:a4 completed (auth)
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:14:bf:84:b2:a4 into blacklist
State: COMPLETED -> DISCONNECTED

The lines:

[INDENT]Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00[/INDENT]

look like something is happening but I don't know what.

I read that dhcp might be setting the interface down, so I tried
not running dhcp against ath0.  That didn't help.

Here is my wpa_supplicant.conf:
> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="__SSID__"
	scan_ssid=1
        key_mgmt=WPA-PSK
	psk="__PSK__"
}

---

### Post by donr on 2006-04-17
I think I found what is happening.  Network Manager is interacting with wpa_supplicant.  Every time NM scans for signals, wpa_supp. disconnects.
As a quick temp fix, I turned NM off and it is working.

See: [http://mail.gnome.org/archives/networkmanager-list/2006-March/msg00385.html](http://mail.gnome.org/archives/networkmanager-list/2006-March/msg00385.html)

---

