---
title: "beginner to ubuntu, problems connecting w/ dsl modem"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by troopakoopa on 2009-11-23
hey, so im a noob with ubuntu (just installed it on my laptop, but still have windows working on home computer) and im having trouble connecting to my wireless network through my qwest dsl modem. ive tried using pppoeconf in the terminal, and it recognizes an eth0 and a wlan0, but says after scanning that the access concentrators on both of them are not responding. i know the ip address and wep key for the modem/router, idk if that helps but thats what i know. ive scanned other threads, but to no avail. any help would be GREATLY appreciated.
thanks!

---

### Post by JBAlaska on 2009-11-24
@ troopakoopa, if you are using a router you don't need to use ppoe on your laptop,

Run these in a terminal and post here:
```
lspci
lsusb
iwconfig
ifconfig

```

[COLOR="Blue"]Edit: Thank You Forum Staff[/COLOR]

---

