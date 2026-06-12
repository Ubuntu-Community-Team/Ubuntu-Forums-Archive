---
title: "Automatically connect to my wlan"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by intimidat0r on 2006-06-26
When I first start my computer Ubuntu (6.06) tries to connect automatically to a seemingly random local wlan. How can I get it to connect to mine?

I searched the forums and saw another thread about /etc/network/interfaces, but it confused me a little.

I also saw another thread about NetworkManager and nm-applet but that seemed like overkill; I'm not a person that needs a fancy GUI for everything - a simple modification of a file will do for me if that's possible.

In case you need it, here is the contents of /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

I don't know what eth2, ath0 and wlan0 are doing there to be honest, but my wireless card is eth1 (and eth0 is my ethernet port).

Thank you. :)

---

### Post by stupidkid on 2006-06-27
Add this under iface eth1 inet dhcp.

wireless_essid <essid>
wireless_key <key>

Make sure you don't use quotation marks with the essid, or it won't work. Oh and of course, omit the brackets.

---

### Post by intimidat0r on 2006-06-27
Thank you, that worked perfectly.

---

