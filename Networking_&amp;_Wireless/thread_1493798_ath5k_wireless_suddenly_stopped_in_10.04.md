---
title: "ath5k wireless suddenly stopped in 10.04"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by BananamansNut on 2010-05-26
Hope this saves some1 an immense amount of time;

First type this;

```
rfkill list
```

check if the problem looks like this

```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: YES

```

If it does (Hard blocked = yes) then definately try popping this into (or editing it if the line already exists;

etc/modprobe.d/options

```
options ath_pci rfkill=0
```

Cross your testicles and reboot(yuck) to make sure everything is fresh - hopefully it works!! (and you don't get testicular torsion).

---

### Post by meggark on 2010-09-12
Cheers dude, you have indeed saved me a lot of time. Much appreciated.

---

### Post by bigfootnmd on 2010-09-12
This is also mentioned in

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

