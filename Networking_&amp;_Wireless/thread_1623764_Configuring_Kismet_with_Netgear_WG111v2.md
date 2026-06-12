---
title: "Configuring Kismet with Netgear WG111v2"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by Kmntal on 2010-11-17
I am trying to configuring Kismet with Netgear WG111v2

Help Please

I have read many many posts, but nothing helped

What should I replace this with

**source=none,none,none**

---

### Post by chili555 on 2010-11-17
First, run this command:```
sudo lspci -C network
```My trimmed output is here:```
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       logical name: [COLOR="Red"]wlan0[/COLOR]
       configuration: broadcast=yes driver=[COLOR="Red"]iwl3945[/COLOR] driverversion=2.6.35
```I then transfered those details to Kismet:> # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=[COLOR="Red"]iwl3945[/COLOR],[COLOR="Red"]wlan0[/COLOR],IntelThe third part, in my case Intel, I don't believe matters much.

Here is another command you could try:```
less /usr/share/doc/kismet/README.gz
```Use the arrow keys to scroll down to Section 12.

---

