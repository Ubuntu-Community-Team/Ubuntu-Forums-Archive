---
title: "WPA and Broadcom 4353 - long time to establish"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by sidowaty on 2010-07-21
Hi (and welcome)!

I have problem with establishing connection through WPA. 
AP: Linksys BEFW 11S4, WPA
PC: Dell Vostro 3500 with Broadcom 4353, using Broadcom STA driver

NetworkManager cannot connect because it uses AP_SCAN=1. I must do it manually via wpa_supplicant.

The way I'm trying to establish connection:
1. kill existing wpa_supplicant
2. stop services network-manager and networking
3. down/up eth1
4. running wpa_supplicant
5. ifconfig, route,  etc.

My wpa_supplicant config file is:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=2

network={
        ssid="Sidowo"
	scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="password"
}
```

And now... It works, but never **connect*** at first time - sometimes 2nd, 9th, 20th, 50th... 
wpa_supplicant gives output like this:

*connect - I mean time, when connection is established(COMPLETED state).

```
root@sid-laptop:/root# wpa_supplicant -Dwext -ieth1 -c /etc/wpa_supplicant/mywpa.conf
Trying to associate with SSID 'Sidowo'
Associated with 00:0f:66:40:1b:e0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID 'Sidowo'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:0f:66:40:1b:e0
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID 'Sidowo'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:0f:66:40:1b:e0
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID 'Sidowo'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:0f:66:40:1b:e0
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID 'Sidowo'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:0f:66:40:1b:e0
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID 'Sidowo'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:0f:66:40:1b:e0
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Could not verify EAPOL-Key MIC - dropping packet
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID 'Sidowo'

```

Maybe it is caused by some timeouts, but really don't know.

Have You any ideas for this problem?
Thanks!

Regards.

---

