---
title: "[SOLVED] WPA with Netgear WG311v2 without Network Manager?"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by Agent86 on 2006-06-30
I'm just about to go through the grind of getting WPA going on my Netgear WG311v2 (ACX chipset) again by following (most) of [this thread]("http://ubuntuforums.org/showthread.php?t=125150") using cvs/svn versions of ndiswrapper, wpasupplicant, and Network Manager. I've done it before, and it works.

My question is, has anyone gotten **_WPA_** working on their WG311v2 in Dapper without using Network Manager? I know the native acx drivers don't support WPA yet, but I was hoping that someone had gotten WPA working with just ndiswrapper and wpasupplicant. Network Manager is a great tool for roaming laptops, but it's just unnecessary for connecting to the same router over and over, so I'd like to ditch it if possible.

---

### Post by awaldram on 2006-06-30
Yes just configure wpa_supplicant.conf

somthing like

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=admin


network={
ssid="Pegasus"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
group=TKIP
psk="Thepresharedkey"
}

---

### Post by Agent86 on 2006-07-01
[QUOTE=awaldram]Yes just configure wpa_supplicant.conf[/QUOTE]Thank you, but that didn't work for my setup. However, knowing that it works for somebody got me pointed in the right direction.

[http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=505&sc=0]("http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=505&sc=0")

My /etc/default/wpasupplicant file```
ENABLED=0
```
My /etc/wpa_supplicant.conf file is either empty or nonexistent (WPA works both ways).

The good stuff is added to the end of /etc/network/interfaces```
auto wlan0
iface wlan0 inet dhcp
wpa-ssid MyESSID
wpa-key-mgmt WPA-PSK
wpa-psk 1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef
wpa-driver wext
```Notice that the last line is "wext" instead of "ndiswrapper". I believe that's a recent kernel development, so you could try it both ways and see which one works. The long jumble after wpa-psk is the ASCII passphrase run through wpa_passphrase.

For all I know, this solution is very specific to my setup, so I'll give those details too

Xubuntu Dapper 6.06, kernel upgraded to 2.6.15-25
Netgear WG311v2 (ACX chipset)
ndiswrapper-1.18 compiled from source (instructions at the [Ubuntu]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and [ndiswrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") wikis.)
using Netgear WG311v2 drivers 2.0.0.7 (WinXP) from their website
wpasupplicant 0.4.8.3 (latest version in the repositories)

---

