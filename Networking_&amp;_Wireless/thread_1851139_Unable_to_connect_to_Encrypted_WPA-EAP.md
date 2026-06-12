---
title: "Unable to connect to Encrypted WPA-EAP"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by ProDG_Yodha on 2011-09-27
Okay,

I have been stuck on this for a week now. I have removed the network-manager because I wanted to start the connection on boot. I edited the /etc/wpa_supplicant.conf and when that failed, I edited the /etc/network/interfaces file.

As I don't have internet connection on that machine, I will type out the relevant parts from /etc/network/interfaces file here..
```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid "PNet"
wpa-ap-scan 1
wpa-scan-ssid 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-eap PEAP
wpa-ca-cert "/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
wpa-phase1 "peapver=0"
wpa-phase2 "auth=MSCHAPV2"
wpa-identity "username"
wpa-password "mypassword"

```

The network is hidden and has the above features. It used to work with the network manager on. But I wanted to have the connection enabled before log-in.

What happens is iwconfig reports the Access point, but
```
 sudo dhclient wlan0
```
returns the following :-
```
 
--- 10.185.32.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms


```

Please help me. I am going mad with this.

Thanks in advance

---

