---
title: "Config troubles with rt2500 WiFi"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by istigkeit on 2010-06-25
I have this little Rosewill PCI WiFi card I've been trying to set up today, giving me a little trouble.

More specifically, it is a Rosewill rnx-g300ex / RaLink rt2561

I understand these should be fairly plug and play, but something about mine isn't quite working like I should am I'm not terribly sure of the solution, so here's what's going on:

The card will establish a connection, and my Connection Information seems to be showing all relevant necessities: network name, driver, mac address, dns, etc.

From reading up today I understand that if I've gotten this far and still can't ping, I might be having config incompatibilities. Ubuntu's wifiDocs pointed me towards iwconfig looking for these lines:

```
Rx invalid nwid
Rx invalid crypt
Rx invalid frag
```as being indicators of config trouble. The inside of /etc/network/interfaces shows only:

```
auto lo
iface lo inet loopback
```Any help on what I ought to do? The wifiDocs file tells me to "change the interfaces file and change the setting with the according iwconfig command," and to be honest I'm not terribly sure how.

Omitted necessary information or other questions, please ask!

Thank you in advance for your time!

---

### Post by istigkeit on 2010-06-26
Justice bump?

---

