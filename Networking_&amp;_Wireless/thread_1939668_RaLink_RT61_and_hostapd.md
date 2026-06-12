---
title: "RaLink RT61 and hostapd"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by Glosshead on 2012-03-12
Hi all!

I have ASUS G31 based on RT61 chip with hostapd on my Ubuntu 11.10. It works fine for a first few minutes after connection. Then Internet does not available via WiFi, local network works fine. And everything is OK via ethernet. I think this is hardware problem but not sure.

Interfaces
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto br0
iface br0 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
bridge_ports eth0 wlan0

```dhcpd.conf
```

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.3 192.168.0.15;
option domain-name-servers 127.0.0.1, 85.21.192.5, 213.234.192.7;
option routers 192.168.0.1;
option broadcast-address 192.168.0.0;
}

```hostapd.conf
```

interface=wlan0
bridge=br0
driver=nl80211
ssid= ***
country_code=RU
#ieee80211d=0
hw_mode=g
channel=11
ignore_broadcast_ssid=1
macaddr_acl=0
wpa=3
wpa_key_mgmt=WPA-PSK
wpa_passphrase= ***
wpa_pairwise=TKIP CCMP

```

---

