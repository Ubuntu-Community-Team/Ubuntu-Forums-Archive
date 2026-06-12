---
title: "Wireless network not working after upgrading to 8.10"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by Erik Agtig on 2009-03-24
Hi, 

I have an old Centrino laptop with a built in Wireless NIC which used to work fine with kubuntu 7.10, using the ipw2200 driver.

I used to use the following /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

This was necessary because WPA was not supported by knetworkmanager in kubuntu 7.0 AFAIK.

After upgrading to 8.10, I cannot get the wlan working. ifconfig -a outputs only eth0, lo, and pan0 (the latter I assume to be a bluetooth device, but I am not sure)

lsmod shows that the ipw2200 module is loaded.

In the future, I would like to use knetworkmanager to manage my connections. I have tried removing the configuration above from /etc/network/interfaces. This allows me to use knetworkmanager for the wired connection, but wireless still does not work.

Any suggestions?

---

