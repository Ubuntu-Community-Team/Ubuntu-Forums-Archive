---
title: "wusb54gc-eu (v3 black ed) can't connect to wap+wpa2"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by ip3t on 2010-09-19
Ubuntu 10.04 >>
i've a linksys wusb54gc v3 1737:0077 (also called eu ) the black version..
adding these three lines on blacklst.conf :

```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```

it's works but only for wep, wpa and wpa2 keys.. not wpa+wpa2  !
in my access point the two possible configuration are these:
- wep
- wpa+wpa2 PSK with TKIP encryption 

i've already read some post, but this problem persists..
should i try with ndiswrapper ?
help me please.
ip3t.

---

