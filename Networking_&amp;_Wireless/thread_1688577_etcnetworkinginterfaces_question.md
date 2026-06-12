---
title: "/etc/networking/interfaces question?"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by MikeyDL on 2011-02-15
Recently I was messing around with my /etc/networking/interfaces and put in two lines for configuring my wlan0 (wireless) adapter which ended up messing it up.  My question is with the exception of the loopback adapter (lo) should you leave the rest of the adapters off so you can manage them through regular networking tools?

---

### Post by dineshs on 2011-02-16
If you want to use network manager your /etc/network/interfaces should have only ```
auto lo
iface lo inet loopback
```
please see [http://ubuntuforums.org/showthread.php?t=1636154](http://ubuntuforums.org/showthread.php?t=1636154)

---

### Post by MikeyDL on 2011-02-16
Thanks for the link!  Finally get the point that it is one or the other now.  Answers some issues I had earlier when I had manually set-up eth0 then was frustrated when I tried to IP using NW and it didn't seem to work.  At least now it makes sense.  :D

---

