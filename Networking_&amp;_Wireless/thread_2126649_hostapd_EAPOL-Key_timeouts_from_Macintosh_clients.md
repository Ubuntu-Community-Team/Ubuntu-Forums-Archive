---
title: "hostapd EAPOL-Key timeouts from Macintosh clients"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by tio289 on 2013-03-17
Hello, I setup my own home mini linux box (Ubuntu server 12.04 LTS) with two wifi atheros cards. All works ok, but my mac from time to time lost connection via WiFi. I use hostapd from official repo, which is version 0.7.3. So I looks in syslog and found this.

```

[I]Mar 17 14:41:17 gateway hostapd: wlan0: STA 00:30:65:1b:69:e4 WPA: EAPOL-Key timeout
[/I][I]Mar 17 14:41:17 gateway hostapd: wlan0: STA 00:30:65:1b:69:e4 WPA: sending 1/4 msg of 4-Way Handshake
[/I][I]Mar 17 14:41:17 gateway hostapd: wlan0: STA 00:30:65:1b:69:e4 IEEE 802.1X: unauthorizing port 
[/I][I]Mar 17 14:41:17 gateway hostapd: wlan0: STA 00:30:65:1b:69:e4 IEEE 802.11: deauthenticated due to local deauth request
[/I]
```
[COLOR=#000000]
I googling and found [this]("http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap-1.git;a=commit;h=4378fc14ebfb355705e7674bf347ea659bcd77bc")[/COLOR]
It is bug in old hostapd version, so I create new from latest old stable 1.1 and 2.0 sources. Both have fixed this bug. You can download amd64 versions here: [http://dev.feldsam.cz/hostapd/](http://dev.feldsam.cz/hostapd/)

If you want create your own, them follow these steps:

Download source of original package and install build dependencies
```

apt-get source hostapd
apt-get build-dep hostapd

```

Enter package directory and remove old sources (all except debian dir)
```

cd hostapd-0.7.3
rm COPYING
rm README
rm -rf hostapd
rm -rf patches
rm -rf src

```

Download and extract hostapd source tar from [http://hostap.epitest.fi/hostapd/](http://hostap.epitest.fi/hostapd/) (I use 2.0 version).
```

wget http://hostap.epitest.fi/releases/hostapd-2.0.tar.gz
tar -xvzf hostapd-2.0.tar.gz
mv hostapd-2.0/* .
rm -r hostapd-2.0

```

Edit build config file *debian/config/linux* and add this line to it
```

CFLAGS += -I/usr/include/libnl3

```


Edit changelog *debian/changelog* and add new version
 
Example:
```

hostapd (1:2.0-1tio) precise; urgency=low


  * Updated to latest 2.0 version


 -- Kristian Feldsam <feldsam@gmail.com>  Sun, 17 Mar 2012 21:58:00 +0100


```

Build package and install
```

dpkg-buildpackage -uc -b
cd ..
dpkg -i hostapd_2.0-1tio_amd64.deb

```

Thats all. I hope that this help somebody :)

---

