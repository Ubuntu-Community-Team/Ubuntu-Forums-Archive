---
title: "Network from console"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2009-05-06
Hi, question:

I set my Linux to automatically boot into console mode (not using gdm/kdm).

Now I want to connect to my wireless router (using dhcp):
I do:
```

 ifconfig eth0_rename up
 iwlist eth0_rename scanning | grep "ESSID"
 iwconfig eth0_rename essid UnencryptedNetwork
 dhclient

```

Now, I  don't get an IP... what did I do wrong?

---

### Post by WitchCraft on 2009-05-07
bump.

---

### Post by Dngrsone on 2009-05-07
Try [this](http://ubuntuforums.org/showthread.php?t=571188).

---

