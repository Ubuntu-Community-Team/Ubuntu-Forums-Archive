---
title: "Wireless connection issue"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by djmoore85 on 2011-10-29
Hey there everyone. It has been a long time since i used Ubuntu, haven't upgraded or been in it since 10.04 netbook remix. Anyway, I missed it, I have been stuck with Windows 7 for school, and found I missed working with Linux in general. Loaded Ubuntu 11.10 onto a Toshiba NB205, and am having an issue with connecting to a wireless network. Here is a printout of the syslog.

```

Oct 29 12:20:27 DanielUbuntuWin7Ulti wpa_supplicant[947]: Trying to authenticate with 00:1d:7e:0b:56:f7 (SSID='DanielElise713' freq=2462 MHz)
Oct 29 12:20:27 DanielUbuntuWin7Ulti kernel: [ 6266.547144] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 1)
Oct 29 12:20:28 DanielUbuntuWin7Ulti kernel: [ 6266.744492] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 2)
Oct 29 12:20:28 DanielUbuntuWin7Ulti kernel: [ 6266.944106] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 3)
Oct 29 12:20:28 DanielUbuntuWin7Ulti kernel: [ 6267.144292] wlan0: authentication with 00:1d:7e:0b:56:f7 timed out
Oct 29 12:20:33 DanielUbuntuWin7Ulti anacron[2927]: Job `cron.daily' started
Oct 29 12:20:33 DanielUbuntuWin7Ulti anacron[3495]: Updated timestamp for job `cron.daily' to 2011-10-29
Oct 29 12:20:34 DanielUbuntuWin7Ulti wpa_supplicant[947]: Trying to authenticate with 00:1d:7e:0b:56:f7 (SSID='DanielElise713' freq=2462 MHz)
Oct 29 12:20:34 DanielUbuntuWin7Ulti kernel: [ 6272.845155] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 1)
Oct 29 12:20:34 DanielUbuntuWin7Ulti kernel: [ 6273.044316] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 2)
Oct 29 12:20:34 DanielUbuntuWin7Ulti kernel: [ 6273.244089] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 3)
Oct 29 12:20:34 DanielUbuntuWin7Ulti kernel: [ 6273.444113] wlan0: authentication with 00:1d:7e:0b:56:f7 timed out
Oct 29 12:20:40 DanielUbuntuWin7Ulti wpa_supplicant[947]: Trying to authenticate with 00:1d:7e:0b:56:f7 (SSID='DanielElise713' freq=2462 MHz)
Oct 29 12:20:40 DanielUbuntuWin7Ulti kernel: [ 6279.152689] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 1)
Oct 29 12:20:40 DanielUbuntuWin7Ulti kernel: [ 6279.352072] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 2)
Oct 29 12:20:41 DanielUbuntuWin7Ulti kernel: [ 6279.552107] wlan0: authenticate with 00:1d:7e:0b:56:f7 (try 3)
Oct 29 12:20:41 DanielUbuntuWin7Ulti kernel: [ 6279.752075] wlan0: authentication with 00:1d:7e:0b:56:f7 timed out
```

Any help getting my wireless or pointing me in the right direction would be much appreciated. Thank yall in advance

---

### Post by djmoore85 on 2011-10-31
*bump* 


If it helps I was able to connect to and not have issues on an open network the other day.

---

