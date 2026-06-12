---
title: "wpa_supplicant choosing wrong ap... please help!"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by chugru on 2006-04-15
I'm in somewhat of a dilema with wpa_supplicant, which incorrectly connects to an unwanted unsecured ap.

My wlan is set up for wpa-psk, and I have managed to get my laptop to connect to it using the following in wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1

ap_scan=1

fast_reauth=1


# Home WLAN: WPA-PSK, PSK as an ASCII passphrase, allow all valid ciphers
network={
        proto=WPA
        ssid="chugru-WAP"
        scan_ssid=0
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="my_private_key"
        priority=5
}

```

In my **/etc/conf.d/net** I have:```
config_eth0=( "dhcp" )
dhcpcd_eth0="-t 10"

modules_ath0=( "wpa_supplicant" )
wpa_supplicant_ath0="-Dmadwifi"
wpa_timeout_ath0=90

preferred_aps_ath0=( "chugru-WAP" )
associate_order_ath0="forcepreferredonly"


mode_ath0="managed"

config_chugru-WAP=( "dhcp" )
```

When I am not at my home wap-psk wlan, I want to be able to connect to any available unsecured wlan, and to do so, I add the following to the end of the wpa_supplicant.conf:```
# Also, when laptop is elsewhere, for "any" Open WLAN:
network={
        ssid=""
        key_mgmt=NONE
}
```
...and I then can connect to the available unsecured wlan in that area.

The delema comes when I leave that last change to wpa_supplicant, and I then boot the laptop back in my home wap-psk environment... The laptop finds and connects to a neighbor's unsecured ap in preference to my wpa-psk secured one.:-? 

I have been unable to either prioritize my wpa-psk wlan or to blacklist my neighbor's unsecured ap, by methods I've tried, so as to make the laptop connect the way I want...

If anyone knows how to do this, please let me know!

Thanks...

---

