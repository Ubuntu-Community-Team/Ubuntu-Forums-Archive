---
title: "see networks but can't connect"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by sandyd on 2009-10-08
Im currently using the bcm43xx drivers for my
```

Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)


```

it sees the networks, but it stalls at the "requesting an ip address" stage
using Wicd.
the networks are connectable using my vista dual boot.
the networks are using open encryption
help?

p.s. don't have wifi at home, so i can only try once in a while...

---

### Post by kevdog on 2009-10-08
Have you tried the wl modules rather than bcm43xx as suggested here:
[http://linuxfans.keryxproject.org/?page_id=27](http://linuxfans.keryxproject.org/?page_id=27)

---

### Post by houstonbofh on 2009-10-09
HAve you enabled the hardware drivers?

System -> Administartion -> Hardware Drivers

It needs the firmware to work properly, but it will appear to work without it.

---

### Post by sandyd on 2009-10-09
aha
missing
b43-fwcutter

installing it now and gonna see how it goes... (p.s. the version that b43-fwcutter downloads is WL)

---

