---
title: "Wireless NIC can't find any networks"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Knez on 2009-02-18
Hi!

I have been trying to solve this problem for a couple of days now without success. I have a Fujitsu-Siemens Amilo D1840 with Ubuntu 8.10 installed. Everything works perfectly except my internal Wireless NIC. Ubuntu finds it but the card doesn't find any networks. My D-Link DWL-G122 USB WiFi card works great, but it would be better if i get the internal card working.

The internal card is a Broadcom BCM4303 rev.2.

//Knez

---

### Post by Knez on 2009-02-18
ok.... so i got some more info.

I get the wlan0 device but when i run "iwlist wlan0 scanning" i get: ```
wlan0 No scan results
```

lspci gives me this:
```
00:0b.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
```

Running "dmesg | grep -e b43 -e wlan" gives me this:
```
[ 2764.988065] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 2820.000033] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 2821.000029] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 2880.000034] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 2881.000031] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 2884.000028] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 2885.000027] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 2940.000087] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 2941.000253] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 2944.000160] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 2945.000276] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 2995.988025] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 2996.988031] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 2999.988033] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 3000.988048] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 3003.988035] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 3004.988054] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 3055.989035] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 3056.988030] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 3059.988044] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 3060.988045] b43legacy-phy0: Radio hardware status changed to ENABLED
[ 3063.988047] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 3064.988043] b43legacy-phy0: Radio hardware status changed to ENABLED
```

Any ideas? ;)

//Knez

---

### Post by superprash2003 on 2009-02-18
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

