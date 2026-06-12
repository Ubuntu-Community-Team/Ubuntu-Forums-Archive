---
title: "Wireless was working, not any more"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by Evil Ninja on 2009-10-13
SO...

Decided to boot up the laptop I have Ubuntu installed on. Previously the wireless was working then stopped working and I was too lazy to fix the problem or asked for help. That was months ago. Boot up the computer, wireless works. A day later, wireless is no longer working. In fact, it doesn't even seem to know I have a wireless card if I were to right click on the network connection symbol (no "Enable Wireless Networking" check box).

Any ideas?

---

### Post by shredder12 on 2009-10-13
Go to System->Administration->hardware drivers 
and see if the wireless driver is enabled..
and post the output of 
```
lspci
```

---

### Post by Iowan on 2009-10-13
**lshw -C network** should provide similar information - limited to networking devices.
I don't suppose you have an ethernet cable plugged in...
**ifconfig -a** (when it works and when it doesn't) may shed some light, too.

---

### Post by witeshark17 on 2009-10-13
Does the computer have a wireless disable button (normally used on planes)? On my keyboard there is; it looks like a graphic of a radio tower.

---

