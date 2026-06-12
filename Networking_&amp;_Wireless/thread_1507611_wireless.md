---
title: "wireless"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by Mr. Bill on 2010-06-11
running 9.04
used ndisgtk to install
ndiswrapper -l yeilds all config file need .config
bcml5:driver installed
      device(14e4:4318)present
iwconfig yeilds     iee 802.11 bg
                    essid:""
                    mode:managed
                    access point: not associated
lsmod yeilds        not listd

lshw yeilds         network: 0 disabled
                    dscription: wireless

i have no connection
i have ndiswrapper 1.56 on stick but cant seem to use it to upgrade or open or anything
I am trying to use you all because my xp crashed but if you are no better than them whats the point

---

### Post by SlidingHorn on 2010-06-11
*does mr. bill voice* ohh noooooo -- ok, now that I got that out of the way...we'll be glad to try to help you out :)

Could you post the *full* outputs of the following commands

```
lspci -nn
```

```
ndiswrapper -l
```

```
sudo lshw -C Network
```

```
ifconfig
iwconfig
```

```
lsmod
```

```
lsb_release -d
```

```
uname -mr
```

i know it's a lot, but it will help us troubleshoot for you :)

---

