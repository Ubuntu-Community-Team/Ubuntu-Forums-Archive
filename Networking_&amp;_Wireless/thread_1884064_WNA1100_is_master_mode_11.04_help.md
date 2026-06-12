---
title: "WNA1100 is master mode 11.04 help"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by harveyd on 2011-11-20
Hi,

I have purchased a WN1100 after reading it was possible to get the Atheros AR9271 is master mode.

When plugging in the WN1100 it is recognised in 'ifconfig -a' as wlan0. 

I read that to use master mode on this device that hostapd is required.

I installed this via apt and created /etc/hostapd/hostapd.conf with the following:-
```

interface=wlan0
driver=nl80211
ssid=MyAP
hw_mode=g
channel=11
wpa=1
wpa_passphrase=MyPasswordHere
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
wpa_ptk_rekey=600
```I then run 'hostapd -dd /etc/hostapd/hostapd.conf' and get the following:-

```
Configuration file: /etc/hostapd/hostapd.conf
Failed to set interface wlan0 to master mode.
nl80211 driver initialization failed.
wlan0: Unable to setup interface.
ELOOP: remaining socket: sock=5 eloop_data=0x9e30a38 user_data=(nil) handler=0x8087b60
```After a bit of research it seemed that I needed to update the ath9k_htc drivers so did the following:-

```
apt-get install linux-headers-generic

wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2

tar jxvf compat-wireless-2.6.tar.bz2 

cd compat-wireless-2011-11-19

./scripts/driver-select ath9k_htc

make

make install

make wlunload

modprobe ath9k_htc
```Now when I ifconfig -a wlan0 does not show.

If I 'make uninstall' from the compat-wireless-2011-11-19 folder and reboot the wlan0 interface returns but hostapd still fails.

Any ideas?

---

