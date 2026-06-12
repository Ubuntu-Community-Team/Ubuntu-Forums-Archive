---
title: "wireless not starting automatically?"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by joemartin on 2011-12-11
New to ubuntu and loving this OS.. Great to be back to Linux...

Lenovo B575 is not starting wireless automatically...

Have to run rmmod acer-wmi to get wireless to start.

I  have also ran this (below) on restart (found in a Mint forum) and this does not  start it automatically either...Need help with a permanent  fix....Thanks.

Upon startup, input these commands:


    rfkill unblock all
    rfkill list
    (sudo) rmmod acer-wmi

    (sudo) ifconfig wlan0 down
    (wait a few seconds)
    (sudo) ifconfig wlan0 up

---

### Post by praseodym on 2011-12-12
Hi,

blacklist the module:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

