---
title: "WPA2 Wireless connection not working"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by fiftyeightz on 2013-02-14
I'm trying to connect to the wireless where I'm staying now. It works for me on Windows but not on Ubuntu 12.04

When I do

```
cat /var/log/syslog
```

I see this in the end:

```
Feb 14 14:40:34 mubuntu wpa_supplicant[1027]: Authentication with 8c:0c:90:54:8a:78 timed out.
Feb 14 14:40:34 mubuntu NetworkManager[870]: <info> (eth0): supplicant interface state: associating -> scanning
Feb 14 14:40:36 mubuntu wpa_supplicant[1027]: Trying to associate with 8c:0c:90:54:8a:78 (SSID='WBH' freq=2437 MHz)
Feb 14 14:40:36 mubuntu wpa_supplicant[1027]: Association request to the driver failed
Feb 14 14:40:36 mubuntu NetworkManager[870]: <info> (eth0): supplicant interface state: scanning -> associating
Feb 14 14:40:41 mubuntu wpa_supplicant[1027]: Authentication with 8c:0c:90:54:8a:78 timed out.
Feb 14 14:40:41 mubuntu NetworkManager[870]: <info> (eth0): supplicant interface state: associating -> scanning
Feb 14 14:40:41 mubuntu wpa_supplicant[1027]: Trying to associate with 8c:0c:90:54:8a:78 (SSID='WBH' freq=2437 MHz)
Feb 14 14:40:41 mubuntu wpa_supplicant[1027]: Association request to the driver failed
Feb 14 14:40:41 mubuntu NetworkManager[870]: <info> (eth0): supplicant interface state: scanning -> associating
```

Any help will be appreciated. Thanx

The wireless connection is WPA2 Personal

---

### Post by ahallubuntu on 2013-02-14
~

---

