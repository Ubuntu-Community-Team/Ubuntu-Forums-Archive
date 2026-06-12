---
title: "Using /etc/network/interfaces to Connect With Two Different Networks"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-08-12
I've read and reread the man interfaces page, but I'm still a little confused. I have two networks I'd like to specify in /etc/network/interfaces, one is WPA-PSK, the other WEP. According to the man page, I *should* just be able to:
```

auto lo
iface lo inet loopback

mapping wlan0
        script /usr/local/sbin/map-scheme
        map HOME wlan0-home
        map WORK wlan0-work

auto wlan0
iface wlan0-home inet dhcp
        wireless-essid XXXXX
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant.conf
        wireless-rate 54M
iface wlan0-work inet dhcp
        wireless-essid XXXXX
        wireless-key XXXXX
        wireless-rate 54M

```Now, all that makes sense to me save one thing: there's no default /usr/local/sbin/map-scheme file. I took that to mean I needed to write my own or find one, but I'm at a loss. Why would the man page be so vague? And, what should go in that map-scheme file?

Help! (Thanks, in-advance.)

EDIT:
Could it be as simple as [this]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")? Well, obviously not because I just tried it. Is there more I need to specify in the mapping section?

---

### Post by moore.bryan on 2009-08-12
SOLVED!

After about an hour of searching through other fora and similar posts/threads, I found [this]("http://forums.debian.net/viewtopic.php?t=17199") thread, which seemed to indicate one could just use the /etc/wpa_supplicant.conf file to do all the heavy lifting. With some modifications, I have it working *flawlessly*. Here's my setup:

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant.conf
        wireless-rate 54M

```/etc/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="HOME"
        key_mgmt=WPA-PSK
        psk="PASSWORD"
}
network={
        ssid="WORK"
        key_mgmt=NONE
        wep_key0=PASSKEY
}

```

---

