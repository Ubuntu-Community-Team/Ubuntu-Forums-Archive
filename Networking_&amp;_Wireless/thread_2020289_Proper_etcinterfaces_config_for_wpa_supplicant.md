---
title: "Proper /etc/interfaces config for wpa_supplicant"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by steerpike on 2012-07-08
Ok, I've been googling around for a few days for a proper /interfaces configuration file in order to connect to a WPA-protected AP using wpa_supplicant. In addition to finding about 10 different configurations, I've also wondered if there is a way to easily connect, via CLI, to a WPA-protected AP.

This seems to be a version issue, as syntax differs between Ubuntu versions, depending on the help article.

Thanks.

---

### Post by praseodym on 2012-07-08
Example for DHCP (prefix "WPA" necessary):
```

auto wlan0
iface wlan0 inet dhcp
     wpa-driver wext
     wpa-ssid YourSSID
     wpa-ap-scan 1
     wpa-proto WPA-PSK
     wpa-pairwise CCMP
     wpa-group CCMP
     wpa-key-mgmt WPA-PSK
     wpa-psk "swordfish"
```
Check pairwise and group with
```
sudo iwlist scan
```
Or, alternatively, with the "wpa_supplicant.conf":

```
auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
```

---

