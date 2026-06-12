---
title: "connecting to wireless sometimes gets stuck in configuring interface"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by milanec on 2013-02-20
Hi guys,

sometimes (let's say 20 percent) when I try to connect to wifi (either at home or at the university), the connecting gets stuck in configuring interface. Only solution is to disable and enable wireless, usually it works after that (sometimes I need to do it two times). At home I use wpa2, at the university I connect to Eduroam where I use my university credentials.

This is what I use:
Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

Is there any solution? To disable and enable wireless usually works but it's not very comfortable.

Thank you

---

### Post by csillva on 2013-02-20
Next time it happens open up a terminal and run this
```
tail /var/log/syslog | grep wpa
```

Or you have some idea when it last happened, look through the syslog for any relevant error messages
```
cat /var/log/syslog | grep wpa
```

---

### Post by milanec on 2013-02-21
I got this error:
Feb 21 12:49:54 milanec wpa_supplicant[1196]: Trying to associate with 00:1b:90:77:a1:b4 (SSID='eduroam' freq=2462 MHz)
Feb 21 12:49:54 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:49:57 milanec wpa_supplicant[1196]: Trying to associate with 00:1b:90:77:a1:b4 (SSID='eduroam' freq=2462 MHz)
Feb 21 12:49:57 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:49:58 milanec wpa_supplicant[1196]: Trying to associate with 00:13:5f:fa:f0:04 (SSID='eduroam' freq=2412 MHz)
Feb 21 12:49:58 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:50:00 milanec wpa_supplicant[1196]: Trying to associate with 00:13:5f:fa:f0:04 (SSID='eduroam' freq=2412 MHz)
Feb 21 12:50:00 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:50:01 milanec wpa_supplicant[1196]: Trying to associate with 00:17:df:2f:18:d3 (SSID='eduroam' freq=2462 MHz)
Feb 21 12:50:01 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:50:04 milanec wpa_supplicant[1196]: Trying to associate with 00:17:df:2f:18:d3 (SSID='eduroam' freq=2462 MHz)
Feb 21 12:50:04 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:50:05 milanec wpa_supplicant[1196]: Trying to associate with 00:26:99:8f:fb:03 (SSID='eduroam' freq=2412 MHz)
Feb 21 12:50:05 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:50:08 milanec wpa_supplicant[1196]: Trying to associate with 00:26:99:8f:fb:03 (SSID='eduroam' freq=2412 MHz)
Feb 21 12:50:08 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:50:09 milanec wpa_supplicant[1196]: Trying to associate with 00:1c:b1:04:19:30 (SSID='eduroam' freq=2412 MHz)
Feb 21 12:50:09 milanec wpa_supplicant[1196]: Deauth request to the driver failed
Feb 21 12:50:11 milanec wpa_supplicant[1196]: Trying to associate with 00:1b:90:77:a1:b4 (SSID='eduroam' freq=2462 MHz)
Feb 21 12:50:21 milanec wpa_supplicant[1196]: Authentication with 00:1b:90:77:a1:b4 timed out.
Feb 21 12:50:22 milanec wpa_supplicant[1196]: Trying to associate with 00:1b:90:77:a1:b4 (SSID='eduroam' freq=2462 MHz)
Feb 21 12:50:22 milanec wpa_supplicant[1196]: Association request to the driver failed

---

### Post by SeijiSensei on 2013-02-21
Broadcom Corporation BCM4313

There have been a spate of problems with this device.  Do a forum search for BCM4313 and see what solutions are available.

---

