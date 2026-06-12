---
title: "wpa_supplicant, authenticating just not setting ip"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by StaticPhilly on 2011-05-08
hello all,

ok im trying to setup wireless and wpa on a box which has ubuntu server installed (no desktops)

so i have made my /etc/wpa_supplicant.conf that contains:
```
ctrl_interface=/var/run/wpa_supplicant

network {
     ssid="MY-WIRELESS-SSID"
     psk=psk-key-generated-by-wpa_passphase
}
```now in /etc/network/interfaces i have
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0 
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid MY-WIRELESS-SSID
pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```now when i reboot, my ethernet connection gets an ip but the wireless im having to type:

```
dhclient wlan0
```to get an ip via dhcp or
```
ifconfig wlan0 192.168.0.100 netmask 255.255.255.0
```for static

can anyone tell me what im doing wrong?
cheers,
Phil

[edit]
after assigning the ip my internet works fine via wireless so its def getting authenticated

---

