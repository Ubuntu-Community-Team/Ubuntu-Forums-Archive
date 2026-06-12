---
title: "Auto-up logical interface in /etc/network/interfaces ??"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by MWP on 2010-08-11
Hi all,

```

iface wlan_home inet static
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
    address 192.168.2.9
    ... etc

iface wlan_adhoc inet static
    address 192.168.3.1
    netmask 255.255.255.0
    ... etc

```

These interfaces can be brought up and down by using, for example, "ifup wlan0=wlan_home".

How do i use the "auto" option in the interfaces file with these iface's?

Doing something like this doesnt work.
```

auto wlan0
iface wlan_home inet static
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
    address 192.168.2.9
    ... etc

```

Any ideas?

Thanks in advance.

---

