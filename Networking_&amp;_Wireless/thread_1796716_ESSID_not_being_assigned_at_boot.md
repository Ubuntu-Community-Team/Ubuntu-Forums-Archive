---
title: "ESSID not being assigned at boot"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by ibznorange on 2011-07-04
So i just threw up my server box again for the first time in a while (new memory ftw), and after much googlefu and remembertizing from last time I got my network up and running. Its a zonet card with an ralink 3062 chipset, connecting to a wpa2 network.

Anyways, my etc/network/interfaces looks like so

```
auto ra0
iface ra0 inet dhcp

wpa-conf managed
wpa-ssid youcanthandlemyssidorthetruth
wpa-key-mgmt WPA-PSK
wpa-psk hexyhexyhexyhexadecimalhexnumbershexhexhexhexhexhexhex

iface lo inet loopback

```

Upon restarting networking (btw when the heck did etc/init.d/networking restart get deprecated?) via the old way or ifdown and ifup on the interface, it works. Upon rebooting however, no connectivity. Running iwconfig before and after restarting networking shows that the configuration isnt assigning it the ssid and such from my interfaces file until i restart networking manually. Not a HUGE issue, but a bit of a pain, especially if i need to reboot remotely and log back in. Cant ssh into a box to restart the network if the network isnt up ;)

Any ideas how to fix this guys?
Thanks in advance

---

