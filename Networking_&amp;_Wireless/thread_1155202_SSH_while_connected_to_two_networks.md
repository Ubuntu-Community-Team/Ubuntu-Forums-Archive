---
title: "SSH while connected to two networks"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by ainsworth on 2009-05-10
I have a laptop and desktop and frequently transfer large amounts of data between the two. The wireless connection isn't fast enough for this so I bought myself a Cat 5 crossover cable which works great. However when they are connected like this, if I use the wireless to browse the internet the ethernet connection stops working, even ping won't work. Presumably because the wireless card provides the default gateway or something. The wireless uses DHCP (192.168.x.x) while the crossover uses static IPs (169.254.x.x). Is it possible to force all connections to IPs in the range 169.254.x.x to use eth0 rather than wlan0?

Cheers

---

### Post by andrewc6l on 2009-05-11
I'm not sure if this changes with the latest networking code, but in the past I've been able to set up this sort of thing (on a temporary basis until the next reboot) with the route command (on the command line).

```
sudo route add -net 169.254.0.0 netmask 255.255.0.0 dev eth0
```

might do what you want.

---

