---
title: "Ubuntu 9.10 Intel 3945 monitor mode"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by jveleg on 2009-11-29
Greetings,

I'm trying to put my Intel 3945 wireless card into monitor mode to capture packets. I have Ubuntu 9.10 and I tried to install ipwraw, ipw3945 and ieee80211 drivers but they cannot be compiled since they need older distributions of Ubuntu. Any idea of how to set my 3945 card into monitor mode in Ubuntu 9.10?

Thanks in advance

---

### Post by chili555 on 2009-11-29
> Any idea of how to set my 3945 card into monitor mode in Ubuntu 9.10?Yes, indeed!```
sudo ifdown wlan0
sudo iwconfig wlan0 mode monitor
```It is a bit hard to get back out to managed mode. If I remember correctly (I am on another computer right now), it is:```
sudo iwconfig wlan0 mode managed
sudo ifup wlan0
```

---

### Post by jveleg on 2009-11-29
Thanks,
Does tcpdump or msgsnarf work for capturing packets from wireless cards when in monitor mode?

Thanks a lot.

---

### Post by chili555 on 2009-11-30
> **jveleg said:**
> Thanks,
Does tcpdump or msgsnarf work for capturing packets from wireless cards when in monitor mode?

Thanks a lot.I have no idea. I have never tried it. I suggest you do just that; try it and see.

---

### Post by samigina on 2009-11-30
Try using the distro "wifislax". It includes esay scripts for wireless tools, like airoway and airoscript... is very easy.

---

