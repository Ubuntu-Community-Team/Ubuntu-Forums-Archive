---
title: "ioctl[SIOCSIWENCODEEXT]: Invalid argument in cli connection"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by CkDGTAT on 2013-08-21
Hi,

```
$ moprobe wilwifi
$ sudo ifconfig wlan0 down
$ sudo ifconfig wlan0 up
$ WIRELESS_IF=wlan0
$ WPA_CONF=/etc/wpa_supplicant/wpa_supplicant.conf
$ sudo wpa_supplicant -Dwext -i${WIRELESS_IF} -c${WPA_CONF}
sudo wpa_supplicant -Dwext -i${WIRELESS_IF} -c${WPA_CONF}



```

My wpa_supplicant.conf is the following

```

network={
  ssid="my_ssid"
  key_mgmt=WPA-EAP
  proto=WPA2
  eap=TTLS
  identity="my_identity"
  password="my_pass"
  anonymous_identity="my_anonymous_identity"
  phase2="auth=MSCHAPV2"
  ca_cert="/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
  ca_cert2="/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
  subject_match="my_server"
  priority=30
}

```

Any help would be great, thank you

---

### Post by gordintoronto on 2013-08-21
I'm sorry, but I did not see a question here. Please clarify?

---

