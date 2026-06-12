---
title: "Internet not working after update"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by Epitaph44 on 2012-02-25
I was running ubuntu 8.x on an old computer of mine.
It was getting internet as soon as I constructed it, and I could use firefox, etc..
When I ran the distribution  to 10.04, I stopped getting a signal.
I have a westell model 6100 modem connecting to eth0 in the back of the computer.
no network device is detected

This is the output of sudo ifup eth0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0

Would retrograding my OS with an old CD cause my connection to work again? What can I do to get my internet connection back?

Thank you

---

### Post by DirtyPC on 2012-02-25
downgrading would bring your connection back, theoretically speaking.
your ethernet driver is clearly not installed, best way would be to get driver from  8.x and install from there

---

