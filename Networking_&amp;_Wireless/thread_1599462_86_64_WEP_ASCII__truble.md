---
title: "86_64 WEP ASCII  truble"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by NewUse on 2010-10-17
Hi, i am not shure, but i think i have find a bug :( (Ubuntu 10.04 x64)

Please, confirm:
I use WEP ACSII 5-character digital (12345) passphrase and wpa_supplicant (WICD) util to connect to WiFi, but I can't connect to my network, before i faild with this profile:
```
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="$_ESSID"
       scan_ssid=$_SCAN
       key_mgmt=NONE
       auth_alg=SHARED
       wep_key0="$_PASSPHRASE"
       wep_tx_keyidx=0
       priority=5
}


```
Then I had to reconnect with stanard profile and it becomes working ... 


Coud you cnfirm? or help to solve this trouble?

---

