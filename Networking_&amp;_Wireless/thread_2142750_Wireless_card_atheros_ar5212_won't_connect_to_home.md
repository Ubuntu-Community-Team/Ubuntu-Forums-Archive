---
title: "Wireless card atheros ar5212 won't connect to home router"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by ritchierope on 2013-05-06
Hello,

i am having a disturbing issue since ubuntu 11.10 that the wifi card in my IBM ThinkPad T43 won't connect to my home router. I am using network manager to connect, it asks for password, tries to connect and then says I am disconnected. I googled around a bit and found a suggestion to connect with a fix IP, with that it manages to connect and after a couple of seconds the connection drops. (internet is not working even when connected) The issue is present with other distros as well. (I tried opensuse as well, the same issue came up.) I cannot find a solution on the web unfortunately.

The card is Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
Subsystem: IBM Device 057e
    Kernel driver in use: ath5k

dmesg:

```
[  205.289723] wlan0: authenticate with AP
[  205.294930] wlan0: send auth to AP (try 1/3)
[  205.299626] wlan0: authenticated
[  205.300322] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  205.304174] wlan0: associate with AP (try 1/3)
[  205.307274] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  205.307284] wlan0: AP denied association (code=12)
[  205.307663] wlan0: deauthenticating from AP by local choice (reason=3)
[  209.526029] wlan0: authenticate with AP
[  209.536697] wlan0: send auth to AP (try 1/3)
[  209.541382] wlan0: authenticated
[  209.541684] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  209.544240] wlan0: associate with AP (try 1/3)
[  209.547270] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  209.547274] wlan0: AP denied association (code=12)
[  209.547396] wlan0: deauthenticating from AP by local choice (reason=3)
[  213.766029] wlan0: authenticate with AP
[  213.773913] wlan0: send auth to AP (try 1/3)
[  213.776206] wlan0: authenticated
[  213.776633] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  213.780252] wlan0: associate with AP (try 1/3)
[  213.783295] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  213.783305] wlan0: AP denied association (code=12)
[  213.783570] wlan0: deauthenticating from AP by local choice (reason=3)
[  217.997778] wlan0: authenticate with AP
[  218.003020] wlan0: send auth to AP (try 1/3)
[  218.009107] wlan0: authenticated
[  218.009503] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  218.012251] wlan0: associate with AP (try 1/3)
[  218.015745] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  218.015754] wlan0: AP denied association (code=12)
[  218.016368] wlan0: deauthenticating from AP by local choice (reason=3)
[  222.233776] wlan0: authenticate with AP
[  222.241520] wlan0: send auth to AP (try 1/3)
[  222.246718] wlan0: authenticated
[  222.247115] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  222.248256] wlan0: associate with AP (try 1/3)
[  222.251303] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  222.251312] wlan0: AP denied association (code=12)
[  222.251578] wlan0: deauthenticating from AP by local choice (reason=3)
[  226.469728] wlan0: authenticate with AP
[  226.475385] wlan0: send auth to AP (try 1/3)
[  226.480194] wlan0: authenticated
[  226.480505] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  226.484255] wlan0: associate with AP (try 1/3)
[  226.487308] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  226.487318] wlan0: AP denied association (code=12)
[  226.487585] wlan0: deauthenticating from AP by local choice (reason=3)
[  230.705979] wlan0: authenticate with AP
[  230.713229] wlan0: send auth to AP (try 1/3)
[  230.715580] wlan0: authenticated
[  230.717080] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  230.720190] wlan0: associate with AP (try 1/3)
[  230.723371] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  230.723380] wlan0: AP denied association (code=12)
[  230.723742] wlan0: deauthenticating from AP by local choice (reason=3)
[  234.941793] wlan0: authenticate with AP
[  234.946947] wlan0: send auth to AP (try 1/3)
[  234.951925] wlan0: authenticated
[  234.952470] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  234.956183] wlan0: associate with AP (try 1/3)
[  234.960950] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  234.960959] wlan0: AP denied association (code=12)
[  234.961319] wlan0: deauthenticating from AP by local choice (reason=3)
[  239.173807] wlan0: authenticate with AP
[  239.178958] wlan0: send auth to AP (try 1/3)
[  239.185735] wlan0: authenticated
[  239.186121] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  239.188248] wlan0: associate with AP (try 1/3)
[  239.191453] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  239.191462] wlan0: AP denied association (code=12)
[  239.192750] wlan0: deauthenticating from AP by local choice (reason=3)
[  243.409797] wlan0: authenticate with AP
[  243.416457] wlan0: send auth to AP (try 1/3)
[  243.421095] wlan0: authenticated
[  243.421399] ath5k 0000:04:02.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  243.424077] wlan0: associate with AP (try 1/3)
[  243.427635] wlan0: RX AssocResp from AP (capab=0x431 status=12 aid=0)
[  243.427645] wlan0: AP denied association (code=12)
[  243.427892] wlan0: deauthenticating from AP by local choice (reason=3)
[  246.084295] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Thank you for your help in advance!

---

### Post by praseodym on 2013-05-06
Try to use pure WPA2-AES encryption. Additionally, the hardware encryption of the driver can be deactivated:
```

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by ritchierope on 2013-05-09
Thank you very much! Deactivating the encryption worked. I will be testing it to see whether it's stable this way. Unfortunatelly there is no WPA2 encryption in the router, only WPA and WEP.
How is it different now without the hardware encryption?

---

### Post by praseodym on 2013-05-09
The device (with its driver) does not additionally encrypt the traffic. Only the WPA encryption will

---

### Post by ritchierope on 2013-05-10
And does that affect my everyday internet use in a way that it became less secure? Not that I am working with anything top secret but it wouldbe nice to know I am surfing safe when I am banking online e.g. :)

---

### Post by praseodym on 2013-05-10
No, using WPA2-AES (CCMP) encryption and the firewall of the router will be enough (here, too)

---

### Post by ritchierope on 2013-05-10
OK, thank you very much for your help, after a long time I can use linux at last again. :)

---

