---
title: "Dont no how to install a Netgear WNDA3100v2"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by Persson on 2013-05-13
Hi Folks! 

I'm new to Ubuntu and I really dont know if I have managed to Install my Netgear wnda3100.
Have tried a couple of "scripts" but just dont know if it's the Netgear stick or if it's the built in network wificard thats up and running..I don't know how to disable the built in one.


Anyone here how wants to help me, and I be very very :Phappy:P

---

### Post by praseodym on 2013-05-13
Please open a terminal with CTRL+ALT+T and show the outputs of
```
uname -a
lsusb
```
Obviously, v2 of this stick need ndiswrapper and the respective windows driver (32 or 64bit)

---

