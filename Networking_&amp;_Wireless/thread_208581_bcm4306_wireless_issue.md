---
title: "bcm4306 wireless issue"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by blu.gecko on 2006-07-03
have a Broadcom 4306 wireless card, with 5.10 I installed the ndiswrapper package and was surfing fine, the new 6.06 shows the broadcom adapter in the network section under admin, but it doesnt work, how do I remove this adapter from the system so I can install the Wlan0 ?

---

### Post by evilghost on 2006-07-03
I have the same wireless card as you.  Add bcm43xx to /etc/modprobe.d/blacklist

```

echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
echo "ndiswrapper" >> /etc/modules

```

Reboot and things should work as expected.

---

