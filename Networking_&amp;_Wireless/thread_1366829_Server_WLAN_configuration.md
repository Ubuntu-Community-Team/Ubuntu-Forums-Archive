---
title: "Server WLAN configuration"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by 1binary0 on 2009-12-28
Hey folks !

Trying to set up WLAN for a Ubuntu Server for the first time.

I've looked around a bit and have successfully found the network and paired it by using **iwconfig wlan0 essid "B Wireless"**.

But when i try to use the **iwconfig wlan0 key s:"M!Y-WPA2-KEY"** i get the following error:
**-bash: !Y-WPA2-KEY: event not found**

The problem appears to be the "!" which is the second character in my key. If i enter the key and leave out the "!" i get no errors.

How do i go about this :confused:

---

### Post by chili555 on 2009-12-29
I believe the **s:** notation is for ASCII WEP keys, not WPA.

---

### Post by 1binary0 on 2009-12-29
That seems to be the case indeed.. Then how can i enter the WPA key??

---

### Post by chili555 on 2009-12-30
> how can i enter the WPA key??In *iwconfig*? You can not, as far as I can tell. This may be helpful: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

You might also look at:```
less /usr/share/doc/wpasupplicant/README.wpa_supplicant.conf.gz
```Also:```
man wpa_cli
```

---

