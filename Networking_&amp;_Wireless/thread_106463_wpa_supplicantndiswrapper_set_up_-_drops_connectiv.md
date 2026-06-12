---
title: "wpa_supplicant/ndiswrapper set up - drops connectivity"
date: 2005-12-20
forum: Networking &amp; Wireless
---

### Post by hw-tph on 2005-12-20
I have an HP nx9105 laptop (a Compaq R3000 model) and it works very well using most Linux distributions. It has a Broadcom chip and while I'm not a big fan of it, I can use ndiswrapper to get the wireless network going and wpa_supplicant to authenticate against my access point.

With recent Ubuntu versions I have had no problems, and I decided to download and test the Kubuntu variant since I haven't used KDE since the days of old. Using the exact same setup as in Ubuntu 5.10, in Kubuntu 5.10 the network works as expected...for a minute. Then connectivity drops. No error messages, no nothing. I can't even ping my access point. The driver I use is the same ("4.0D" 32bit Windows driver), the config files are exactly the same as in Ubuntu. But it just won't work properly. I have come to the point where I must use my fallback wired Ethernet but I'd rather not.

Some information:
[list][*]Kernel: Linux 2.6.12-10-k7 (from the official Ubuntu repositories)
[*]ndiswrapper-utils 1.1-4ubuntu2, using bcmwl5 driver
[*]wpasupplicant 0.4.5-0ubuntu1[/list]

/etc/wpa_supplicant.conf: ```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
network={
        ssid="networkname"
        psk=reallyreallylonglistofcharacters
        key_mgmt=WPA-PSK
        proto=WPA
}
```

/etc/default/wpasupplicant:```
ENABLED=1
OPTIONS=""
```
I have used the above with a lot of options enabled but decided they didn't help much as I don't use wpa_supplicant as a daemon but rather starting it from the file below and specifying the options there.

Snippet from /etc/network/interfaces:```
# WLAN
auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -B -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Any takers?


Håkan

---

