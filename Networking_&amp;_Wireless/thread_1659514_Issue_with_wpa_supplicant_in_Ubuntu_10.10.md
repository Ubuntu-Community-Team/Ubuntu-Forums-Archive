---
title: "Issue with wpa_supplicant in Ubuntu 10.10"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by kedarkekan on 2011-01-04
Hi all,

I am running Ubuntu 10.10.
Recently compiled ath5k driver and trying to connect using wpa_supplicant.

i can connect using the native network manager, but facing problem to connect using built wpa_supplicant.

wpa_supplicant.conf file:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=1


network={
    ssid="safari"
    psk=25d84bde40148a4c90e86309d8af883413b0371847eab0ed54cdea4da7d61431
}


Association is fine, but the connection fails due to below issue:

State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x1203 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:15:c7:fe:e0:60 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys



Details:
wpa_supplicant-0.6.10
compat-wireless-2010-12-26
2.6.35-23-generic


Any help will be appreciated !

---

