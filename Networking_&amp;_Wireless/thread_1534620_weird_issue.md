---
title: "weird issue"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by makaveli0129 on 2010-07-19
Ok so i have my wireless card using driver i do iwconfig and i get this:
```

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

so it's connected and the driver for the wireless is working fine 

lsch -C Network shows this:

```

 *-network
       description: Wireless interface
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth2
       version: 01
       serial: 00:1e:e5:a9:3a:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl1 

```

but the weird thing is i have no icon on my screen to connect to my network like i usually do and i can't figure out where the icon went and why i can't connect any ideas?

---

### Post by Iowan on 2010-07-19
Are you talking about the Network Manager icon?
*Sometimes* you can fix the problem by adding a "Notification Area" to the top panel.

---

### Post by makaveli0129 on 2010-07-21
> **Iowan said:**
> Are you talking about the Network Manager icon?
*Sometimes* you can fix the problem by adding a "Notification Area" to the top panel.

yes i am referring to the Network manager where it shows the little bars and all that and you can click on it and it will show the networks in range. One day it just disappeared.

---

### Post by makaveli0129 on 2010-07-21
> **makaveli0129 said:**
> yes i am referring to the Network manager where it shows the little bars and all that and you can click on it and it will show the networks in range. One day it just disappeared.

that worked and i can connect now. Where did the old one go with the bars and everything else? That's what i'm curious about it just up and disappeared.

---

