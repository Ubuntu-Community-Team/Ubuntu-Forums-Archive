---
title: "newbie dailup help no broadbandI'm a newbie and need help with dialup. Using ubuntu 1"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by captainstorey on 2010-05-18
I'm a newbie and need help with dialup. Using ubuntu 10.04 with usb zoom 3095 dialup modem. I can connect to the internet and stay connected but can't view websites or download e-mails. I have tried gnome-ppp and wvdial via root and put a tick in the dip group users also. I'm using wvdial 1.61 and edited the config file for phone number, password and username. When opening any web browser I just have a blank screen and the data light rarely flashes. Any help would be great. Not all of us have broadband, so I rely on friends for updates etc. Modem works fine in windows and the data light flashes like crazy, but want to ditch windows fully. Thanks. Captain.

---

### Post by dineshs on 2010-05-18
> **captainstorey said:**
>  I can connect to the internet and stay connected but can't view websites or download e-mails. 
once connected try to ping this open DNS```
ping 4.2.2.1
```
If you are getting reply from 4.2.2.1,
```
gksudo gedit /etc/resolv.conf
```
edit the file so that it contains only this
```
nameserver 4.2.2.1 -c5
```

---

