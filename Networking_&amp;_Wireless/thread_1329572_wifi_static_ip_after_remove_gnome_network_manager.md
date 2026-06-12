---
title: "wifi static ip after remove gnome network manager"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2009-11-17
Can some one share a configuration file so that I can know how do I give entry for my wifi 
since I have removed network-manager-gnome
and /etc/network/interfaces I have created manually entries for LAN which do work but I am not clear for the wifi part I have to do it manually

---

### Post by chili555 on 2009-11-17
I think all you need are *interfaces* and *resolv.conf* correctly set up. Here are mine with a few details disguised:```
/etc/resolv.conf:

nameserver 192.168.1.254
``````
/etc/network/interfaces:


auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid mylilrouter
wireless-key 096C7Fxxxxxxxxxxxxx

#auto eth0
iface eth0 inet dhcp
```If you are using WPA, the details are a bit more complex. Please post back if you need more.

---

### Post by tapas_mishra on 2009-11-18
> **chili555 said:**
> I think all you need are *interfaces* and *resolv.conf* correctly set up. Here are mine with a few details disguised.
I thought I had to edit wpa_supplicant.conf how can I know what encryption is being used I forgot it after setting it.

---

